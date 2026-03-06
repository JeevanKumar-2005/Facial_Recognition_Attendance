# Facial Recognition Attendance System

A Django-based web application for automated attendance marking using facial recognition technology.

## Features
- User registration with facial image capture
- Real-time attendance marking via webcam
- Admin dashboard for managing users and attendance records
- SQLite/MySQL database support
- Responsive web interface

## Prerequisites
- **Python 3.9** (64-bit)
- **Git** (for cloning)
- **Webcam** (for face capture and attendance)
- **Visual Studio Build Tools** (for compiling dlib on Windows)

## Quick Setup (Windows)

### 1. Clone Repository
```bash
git clone <repository-url>
cd facial_recognititon_attendace
```

### 2. Install Python Dependencies
```powershell
# Upgrade pip
python -m pip install --upgrade pip setuptools wheel

# Install core dependencies
python -m pip install -r requirements_without_dlib.txt
```

### 3. Install dlib (Critical)
dlib is required for face recognition. Download the pre-built wheel:
- Visit: https://www.cgohlke.com/
- Download: `dlib-19.24.2-cp39-cp39-win_amd64.whl`
- Install:
```powershell
python -m pip install dlib-19.24.2-cp39-cp39-win_amd64.whl
python -m pip install face-recognition==1.3.0
```

### 4. Configure Database
For quick testing with SQLite:
```powershell
$env:USE_SQLITE = '1'
```

### 5. Setup Database
```powershell
python manage.py migrate
python manage.py createsuperuser  # Optional
```

### 6. Run Server
```powershell
python manage.py runserver
```
Access at: http://127.0.0.1:8000/

## Detailed Setup Guide

### Windows Setup
See `README_WINDOWS_INSTALL.md` for comprehensive Windows installation instructions including:
- Alternative dlib installation methods
- MySQL setup
- Troubleshooting common issues

### Linux/Mac Setup
1. Install system dependencies:
```bash
# Ubuntu/Debian
sudo apt-get install build-essential cmake libgtk-3-dev libboost-all-dev

# macOS
brew install cmake boost
```

2. Install Python packages:
```bash
pip install -r requirements.txt
```

## Project Structure
```
facial_recognititon_attendace/
├── Facial_Recognition_Attendance/  # Django project settings
├── Face_App/                      # Main application
│   ├── models.py                  # Database models
│   ├── views.py                   # View logic
│   ├── templates/                 # HTML templates
│   ├── static/                    # CSS/JS assets
│   └── migrations/                # Database migrations
├── media/                         # User uploaded images
├── db.sqlite3                     # SQLite database
├── manage.py                      # Django management script
├── requirements.txt               # All dependencies
└── requirements_without_dlib.txt  # Dependencies excluding dlib
```

## Usage

### User Registration
1. Navigate to `/Registeration2`
2. Enter user details
3. Capture facial image using webcam
4. Submit registration

### Attendance Marking
1. Go to `/Attendance`
2. Allow camera access
3. System will detect and mark attendance automatically

### Admin Functions
- Login at `/Admin_Login`
- View users and attendance records
- Manage system settings

## API Endpoints
- `/` - Home page
- `/Admin_Login` - Admin login
- `/Employee_Login` - User login
- `/Registeration` - User registration
- `/Attendance` - Attendance marking
- `/View_Attendance` - View attendance records

## Configuration

### Database Settings
Edit `Facial_Recognition_Attendance/settings.py`:
- Default: MySQL (requires XAMPP/WAMP setup)
- SQLite: Set environment variable `USE_SQLITE=1`

### Media Settings
- Images stored in `media/user_images/`
- Configure paths in `Face_App/views.py` if needed

## Troubleshooting

### Common Issues
1. **"face_recognition not installed"**
   - Ensure dlib is properly installed
   - Restart Django server
   - Check Python version compatibility

2. **Database connection errors**
   - For SQLite: Set `$env:USE_SQLITE = '1'`
   - For MySQL: Ensure service is running

3. **Camera not working**
   - Check webcam permissions
   - Ensure OpenCV can access camera
   - Test with `python -c "import cv2; print(cv2.VideoCapture(0).isOpened())"`

4. **Build errors**
   - Install Visual Studio Build Tools
   - Use pre-built dlib wheel
   - Ensure CMake is installed

### Verification Commands
```powershell
# Check installations
python -c "import dlib; print('dlib:', dlib.__version__)"
python -c "import face_recognition; print('face_recognition: OK')"
python -c "import cv2; print('OpenCV:', cv2.__version__)"

# Test Django
python manage.py check
python manage.py shell -c "import face_recognition; print('Django: OK')"
```

## Dependencies
- Django 4.1.13
- dlib 19.24.2+
- face-recognition 1.3.0
- OpenCV 4.8.0
- NumPy 1.24.3
- Pillow 10.0.1
- MySQL client (optional)

## Contributing
1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Support
For issues and questions:
- Check `README_WINDOWS_INSTALL.md` for Windows-specific help
- Verify all prerequisites are met
- Test individual components before full setup</content>
<parameter name="filePath">c:\project\facial_recognititon_attendace\README.md