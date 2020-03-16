## taskrc.md for circuit-playground.explore

### Todo:
* How can we talk to the embedded terminal in python?  In shell?
* How to get autocomplete on the

### Reference stuff
* The device auto-boots whatever is in `e:\code.py`, and if that changes it restarts the app.  This is because it's running the bootloader which encodes that behavior in the form of [CircuitPython](https://github.com/adafruit/circuitpython)
* The `mu` editor is installed on Stableburner. It has a built-in terminal to talk to the device
* [Using it with vscode](https://www.hanselman.com/blog/UsingVisualStudioCodeToProgramCircuitPythonWithAnAdaFruitNeoTrellisM4.aspx)

* Bootloader is here [./adafruit-circuitpython-circuitplayground_express-en_US-5.0.0.uf2]()


```bash
function errExit {
    echo "ERROR: $@" >&2
    exit 1
}

function mount_E {
    # Help the circuit playground shows up as E: on stableburner:
    (
        sudo mkdir -p /mnt/e && sudo chmod oug+rwx /mnt/e
        sudo mount -t drvfs E: /mnt/e && cd / && sudo ln -sf /mnt/e /e 2>/dev/null
    )
    ls -l /e/*
}

function gpa {
    # Help Because the code files live on the device beyond the reach of git, we must copy them to devmirror/ and commit them that way
    cd $taskrc_dir
    if [[ ! -f drive_e/code.py ]]; then
        return $(errExit "Can't find drive_e/code.py")
    fi
    mkdir -p devmirror
    cp drve_e/*py devmirror/
    git commit -am sync; git push
}

```
