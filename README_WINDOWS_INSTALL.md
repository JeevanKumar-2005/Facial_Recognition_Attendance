Windows-specific dlib installation instructions

If you are running this project on Windows, the `face-recognition` library needs `dlib`.
`dlib` often requires building C++ extensions and can fail to build without Microsoft Visual C++ Build Tools.

Options to install `dlib` on Windows:

1) Preferred: Download a pre-built wheel (no compiler needed)
   - Open: https://www.lfd.uci.edu/~gohlke/pythonlibs/#dlib or https://www.cgohlke.com/
   - Download the wheel that matches your Python version and architecture (e.g., `dlib-19.24.2-cp39-cp39-win_amd64.whl` for Python 3.9 64-bit)
   - Save the .whl to the project folder and run:
     ```
     pip install dlib-19.24.2-cp39-cp39-win_amd64.whl
     pip install face-recognition==1.3.0
     ```

2) Install Build Tools and compile from source
   - Download Visual Studio Build Tools: https://aka.ms/vs/stable/vs_BuildTools.exe
   - Install the **C++ build tools** workload (MSVC, Windows SDK, CMake tools)
   - After install, run:
     ```
     pip install dlib
     pip install face-recognition==1.3.0
     ```

3) Use conda / miniconda (easiest if you prefer reproducible envs)
   - Create environment: `conda create -n fr python=3.9`
   - Activate: `conda activate fr`
   - Install prebuilt `dlib` (conda-forge): `conda install -c conda-forge dlib`
   - Then install remaining requirements: `pip install -r requirements_without_dlib.txt` and `pip install face-recognition==1.3.0`

Running the project (once dependencies are installed):

1. Ensure dependencies are installed:
   - `pip install -r requirements_without_dlib.txt`
   - Follow instructions above to install `dlib` and then `pip install face-recognition==1.3.0` if commented out in `requirements_without_dlib.txt`.

2. If you don't have a local MySQL server available, you can use the included SQLite DB for quick testing:
   - On PowerShell (temporary for this session): `$env:USE_SQLITE = '1'`
   - Or set it permanently in System Environment Variables: `USE_SQLITE=1`

3. Apply migrations:
   - `python manage.py migrate`

4. Create a superuser (optional):
   - `python manage.py createsuperuser`

5. Run the dev server:
   - `python manage.py runserver`

If the server fails at startup due to `dlib`/`face_recognition` imports, verify `dlib` is installed and importable:

```python
python -c "import dlib; print(dlib.__version__)"
```

If you want, I can attempt the server run here now using SQLite (no MySQL required).