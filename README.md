script.module.pydevd
==================

Kodi support for PyDev debugging in Eclipse/Aptana.

How to use:
-----------

 1. Add script.module.pydevd as a requirement to the module under test:

    ```xml
    <!-- addon.xml -->
    <addon id="your.addon">
        <requires>
            <import addon="script.module.pydevd" version="2.0.0"/>
        </requires>
    </addon>
    ```

 2. Then in the code under test add these lines at the beginning:
    ```python
    import pydevd
    pydevd.settrace(stdoutToServer=True, stderrToServer=True, suspend=False)
    ```

 3. Start the debug server in Eclipse.

    If the debug server is not running when you call settrace then you'll encounter:

    ```python
    Error Type: <class 'socket.error'>
    Error Contents: [Errno 111] Connection refused
    ```

 4. Set breakpoints in Eclipse.

    *This step is optional if you omit the `suspend=False` argument in the `pydevd.settrace` function or set it to `True`. Then a breakpoint will be emulated as soon as that function is called.*

 5. Use Eclipse debug perspective to move through code.

See http://pydev.org/ for details.

Known Issues:
-------------

When attempting to exit or shutdown, Kodi will often freeze after a debug session
has been initiated.

Images in Kodi skins often fail to render during a debug session. If you want to
verify that images are being rendered then do not run under a pydev debug session.

Trademarks:
----------

"Python" is a registered trademark of the PSF. The Python logos (in several variants) are trademarks of the PSF as well. The logos are not registered, but registration does not equal ownership of trademarks.

www.python.org/psf/trademarks/
