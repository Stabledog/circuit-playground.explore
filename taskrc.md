## taskrc.md for circuit-playground.explore

### Reference stuff
- The device auto-boots whatever is in `e:\code.py`, and if that changes it restarts the app.  This is because it's running the
- The `mu` editor is installed on Stableburner. It has a built-in terminal to talk to the device
- [Using it with vscode](https://www.hanselman.com/blog/UsingVisualStudioCodeToProgramCircuitPythonWithAnAdaFruitNeoTrellisM4.aspx)

- Bootloader is here [./adafruit-circuitpython-circuitplayground_express-en_US-5.0.0.uf2]


```bash
function mount_E {
    # Help the circuit playground shows up as E: on stableburner:
    sudo mkdir -p /mnt/e && sudo chmod oug+rwx /mnt/e
    sudo mount -t drvfs E: /mnt/e && cd / && sudo ln -sf /mnt/e /e

}
```
