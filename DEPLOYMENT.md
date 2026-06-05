# Deploy Soccer 2026 Match Predictor to Streamlit Community Cloud

This guide will help you deploy your Streamlit app online for free using Streamlit Community Cloud.

## Prerequisites

- A GitHub account
- Your code pushed to a GitHub repository
- The model files (`models/match_predictor.pkl` and `models/team_data.pkl`) in your repository

## Files Required for Deployment

✅ All required files are already created:
- `app.py` - Main Streamlit application
- `requirements.txt` - Python dependencies
- `.streamlit/config.toml` - Streamlit configuration
- `models/match_predictor.pkl` - Trained ML model
- `models/team_data.pkl` - Team statistics data

## Deployment Steps

### 1. Push Your Code to GitHub

```bash
# Initialize git repository (if not already done)
cd 02_football_lab_june/03_jupyter_notebook
git init

# Add all files
git add .

# Commit changes
git commit -m "Add Soccer 2026 Match Predictor app"

# Create a new repository on GitHub, then:
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git branch -M main
git push -u origin main
```

### 2. Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io)
2. Sign in with your GitHub account
3. Click "New app"
4. Fill in the deployment form:
   - **Repository**: Select your GitHub repository
   - **Branch**: `main` (or your default branch)
   - **Main file path**: `02_football_lab_june/03_jupyter_notebook/app.py`
   
5. Click "Deploy!"

### 3. Wait for Deployment

- Streamlit will install dependencies from `requirements.txt`
- The app will be live at: `https://YOUR_USERNAME-YOUR_REPO_NAME.streamlit.app`
- Deployment typically takes 2-5 minutes

## Important Notes

### Model Files Size
- GitHub has a 100MB file size limit
- If your model files are too large, consider:
  - Using Git LFS (Large File Storage)
  - Hosting models on cloud storage (AWS S3, Google Cloud Storage)
  - Retraining with a simpler model

### Check Model File Sizes
```bash
ls -lh models/
```

If files are over 100MB, you'll need to use Git LFS:

```bash
# Install Git LFS
git lfs install

# Track large files
git lfs track "models/*.pkl"
git add .gitattributes
git add models/
git commit -m "Add model files with Git LFS"
git push
```

## Troubleshooting

### App Won't Start
- Check the logs in Streamlit Cloud dashboard
- Verify all dependencies are in `requirements.txt`
- Ensure model files are committed to the repository

### Model Not Found Error
- Verify the path in `app.py` matches your repository structure
- Check that model files are in the `models/` directory

### Memory Issues
- Streamlit Community Cloud has 1GB RAM limit
- Consider optimizing your model or upgrading to a paid plan

## Alternative Deployment Options

If Streamlit Community Cloud doesn't work for you:

1. **Hugging Face Spaces** - Free hosting with GPU support
2. **Render** - Free tier available
3. **Railway** - Free tier with $5 credit
4. **Heroku** - Paid plans only (no longer free)

## Your App URL

Once deployed, your app will be accessible at:
```
https://YOUR_USERNAME-YOUR_REPO_NAME.streamlit.app
```

Share this URL with anyone to let them use your Soccer Match Predictor!

## Updating Your App

To update your deployed app:
```bash
# Make changes to your code
git add .
git commit -m "Update app"
git push
```

Streamlit Cloud will automatically redeploy your app when you push changes to GitHub.