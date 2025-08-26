# kubectl-neat-for-web

kubectl-neat-for-web is a static HTML/CSS/JavaScript web application that cleans up verbose Kubernetes YAML/JSON outputs directly in the browser. It operates entirely client-side with no backend dependencies.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Essential Setup
- **No build process required** - This is a static HTML application that runs directly in browsers
- **No package.json or dependencies** - Uses CDN resources: js-yaml@4.1.0, jszip@3.10.1, tailwindcss
- **No installation needed** - Application works by opening `index.html` in any modern browser

### Running the Application
- **Local testing**: 
  - `cd /home/runner/work/kubectl-neat-for-web/kubectl-neat-for-web`
  - `python3 -m http.server 8080` (starts in ~1 second)
  - Open `http://localhost:8080` in browser
- **Alternative server**: `npx serve -s . -p 8080` (takes ~3 seconds first run due to package installation)
- **Direct file**: Open `index.html` directly in browser (some features may be limited due to file:// protocol restrictions)

### Development Workflow
- **Edit files**: Modify `index.html` directly - all application code is in this single file
- **Test changes**: Refresh browser - changes are immediately visible
- **No compilation**: No build step required
- **No linting tools**: No configured linters (consider adding HTML/JS validation if needed)

## Validation

### ALWAYS test complete user scenarios after making changes:
1. **Paste YAML scenario**:
   - Paste Kubernetes YAML with verbose fields (`status`, `managedFields`, `creationTimestamp`, etc.)
   - Click "🧹 Neaten" button
   - Verify output removes noisy fields but keeps essential configuration
   - Test "📋 Copy to Clipboard" functionality
   - Test "📄 Download as YAML" functionality

2. **File upload scenario**:
   - Switch to "Upload YAML files/folders" mode
   - Upload .yaml/.yml files
   - Verify processing and download options appear
   - Test multiple file handling and ZIP download functionality

3. **Multi-document YAML scenario**:
   - Test YAML with `---` separators
   - Verify each document is processed correctly

### Functionality Notes
- **CDN Dependencies**: Application works with fallback text processing if CDN resources (js-yaml, jszip, tailwindcss) are blocked
- **Internet connection**: Not required for basic operation, but full YAML parsing requires CDN access
- **Browser compatibility**: Works in all modern browsers with JavaScript enabled
- **File processing**: Completely client-side - no data sent to servers

## Common Tasks

### Repository Structure
```
.
├── .gitignore          # Ignores .DS_Store files
├── README.md           # Project documentation
├── index.html          # Complete application (HTML/CSS/JS)
└── image.png           # Screenshot for documentation
```

### Key Application Features
- **YAML cleaning**: Removes `status`, `metadata.managedFields`, `metadata.creationTimestamp`, `resourceVersion`, `uid`, `generation`
- **Multi-document support**: Handles YAML files with `---` separators
- **File operations**: Upload single/multiple files, upload folders, download individual/ZIP files
- **Client-side processing**: No backend required, works offline (with CDN fallback)

### Testing Commands
```bash
# Start local server (immediate)
python3 -m http.server 8080

# Alternative server (3 seconds first run)
npx serve -s . -p 8080

# Verify server response
curl -s http://localhost:8080 | head -5
```

### Code Organization in index.html
- **HTML structure**: Lines 1-100 (UI layout, form elements)
- **Styling**: Inline Tailwind CSS classes
- **JavaScript functions**: Lines 100-460
  - `neat()`: Main YAML processing function
  - `stripFields()`: Removes verbose Kubernetes fields
  - `processFiles()`: Handles file uploads
  - `downloadFile()`, `downloadAsZip()`: Download functionality
  - `copyToClipboard()`: Copy functionality

### Making Changes
- **UI modifications**: Edit HTML structure and Tailwind classes
- **YAML processing logic**: Modify `stripFields()` function around line 350
- **File handling**: Update `processFiles()` function around line 180
- **Add new features**: Insert JavaScript functions before closing `</script>` tag

### Debugging
- **Browser console**: Check for JavaScript errors
- **Network tab**: Verify CDN resource loading
- **Test with sample data**: Use provided Kubernetes YAML examples
- **Fallback mode**: Test functionality when CDN resources are blocked

## Validation Checklist
Always complete these steps after making changes:
- [ ] Start local server successfully
- [ ] Open application in browser without errors
- [ ] Test YAML paste and clean functionality
- [ ] Verify copy to clipboard works
- [ ] Test file download functionality
- [ ] Switch between paste/upload modes
- [ ] Test with multi-document YAML (containing `---`)
- [ ] Verify application works with blocked CDN resources (fallback mode)

## Important Notes
- **No CI/CD**: No GitHub Actions or automated builds configured
- **No tests**: No automated test suite exists
- **Single file**: Entire application contained in `index.html`
- **Static hosting**: Designed for GitHub Pages deployment
- **No server**: Pure client-side application, no backend API