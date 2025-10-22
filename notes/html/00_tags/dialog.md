# `<dialog>`

## Key Topics

+ [Definition and Purpose](#definition-and-purpose)
+ [Syntax and Variants](#syntax-and-variants)
+ [Attributes](#attributes)
+ [Content Model](#content-model)
+ [Context](#context)
+ [Behavior and Semantics](#behavior-and-semantics)
+ [Examples](#examples)
+ [Notes](#notes)

---

## Definition and Purpose

The `<dialog>` element represents a dialog box or other interactive component, such as a modal, alert, inspector, or subwindow. It provides a native, accessible way to create modal and non-modal dialogs without relying on JavaScript-heavy solutions. The element manages focus, stacking context, and accessibility automatically when used with the native API methods.

---

## Syntax and Variants

+ **Standard syntax**: `<dialog>...</dialog>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain any flow content
+ **No self-closing variant**: Must have closing tag
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **Core attributes**:
  - `open` (optional): Indicates the dialog is active and visible
  - `returnValue` (optional): Return value from the dialog when closed

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.

+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Flow content
+ **Allowed content**:
  - Headings, paragraphs, lists
  - Forms, buttons, inputs
  - Images, videos, other embedded content
  - Any valid HTML content typically found in dialogs
+ **Restricted content**: No specific restrictions beyond normal HTML validation
+ **Common patterns**: Typically contains header, content area, and footer with actions

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Directly within `<body>` for modal dialogs
  - Within specific sections for contextual dialogs
  - As children of other interactive components
+ **Nesting relationships**:
  - Can contain most HTML elements
  - Often contains `<form>` elements with `method="dialog"`
  - Typically has a semantic structure with heading and actions

---

## Behavior and Semantics

+ **Default display**: None (hidden when no `open` attribute)
+ **Default styling**:
  - `display: none` (when closed)
  - `display: block` (when open, with browser-specific positioning)
  - Centered in viewport with backdrop
  - Browser-specific default styles (often with padding and border)
+ **Semantic meaning**:
  - Represents a dialog or interactive component
  - Indicates content that should be separated from main flow
  - Provides native dialog semantics for accessibility
+ **Accessibility role**:
  - Implicit ARIA role: `dialog`
  - Automatically manages focus and ARIA attributes
  - Backdrop prevents interaction with background content
+ **Native methods**:
  - `show()`: Shows as non-modal dialog
  - `showModal()`: Shows as modal dialog with backdrop
  - `close()`: Closes the dialog
  - `returnValue`: Gets/sets return value

---

## Examples

**Basic modal dialog:**
```html
<dialog id="basicDialog">
  <h2>Basic Dialog</h2>
  <p>This is a simple modal dialog example.</p>
  <button onclick="document.getElementById('basicDialog').close()">Close</button>
</dialog>

<button onclick="document.getElementById('basicDialog').showModal()">
  Open Basic Dialog
</button>

<style>
#basicDialog {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

#basicDialog::backdrop {
  background-color: rgba(0, 0, 0, 0.5);
}
</style>
```

**Confirmation dialog with form:**
```html
<dialog id="confirmDialog">
  <form method="dialog">
    <h2>Confirm Action</h2>
    <p>Are you sure you want to delete this item? This action cannot be undone.</p>
    <div class="dialog-actions">
      <button value="cancel">Cancel</button>
      <button value="confirm" class="danger">Delete</button>
    </div>
  </form>
</dialog>

<button onclick="document.getElementById('confirmDialog').showModal()">
  Delete Item
</button>

<script>
const confirmDialog = document.getElementById('confirmDialog');

confirmDialog.addEventListener('close', () => {
  if (confirmDialog.returnValue === 'confirm') {
    console.log('Item deleted');
    // Perform deletion logic
  }
});
</script>

<style>
#confirmDialog {
  border: none;
  border-radius: 12px;
  padding: 0;
  max-width: 400px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

#confirmDialog form {
  padding: 24px;
}

#confirmDialog h2 {
  margin: 0 0 12px 0;
  color: #333;
  font-size: 1.5em;
}

#confirmDialog p {
  margin: 0 0 20px 0;
  color: #666;
  line-height: 1.5;
}

.dialog-actions {
  display: flex;
  gap: 12px;
  justify-content: flex-end;
}

.dialog-actions button {
  padding: 10px 20px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background: white;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.2s;
}

.dialog-actions button:hover {
  background: #f5f5f5;
}

.dialog-actions .danger {
  background: #dc3545;
  color: white;
  border-color: #dc3545;
}

.dialog-actions .danger:hover {
  background: #c82333;
}

#confirmDialog::backdrop {
  background: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(2px);
}
</style>
```

**Settings dialog with multiple sections:**
```html
<dialog id="settingsDialog">
  <div class="dialog-header">
    <h2>Settings</h2>
    <button class="close-button" onclick="document.getElementById('settingsDialog').close()">
      ×
    </button>
  </div>
  
  <div class="dialog-content">
    <section class="settings-section">
      <h3>Appearance</h3>
      <div class="setting">
        <label>
          <input type="checkbox" name="darkMode"> Dark mode
        </label>
      </div>
      <div class="setting">
        <label>Font size</label>
        <select name="fontSize">
          <option value="small">Small</option>
          <option value="medium" selected>Medium</option>
          <option value="large">Large</option>
        </select>
      </div>
    </section>
    
    <section class="settings-section">
      <h3>Notifications</h3>
      <div class="setting">
        <label>
          <input type="checkbox" name="emailNotifications" checked> Email notifications
        </label>
      </div>
      <div class="setting">
        <label>
          <input type="checkbox" name="pushNotifications"> Push notifications
        </label>
      </div>
    </section>
  </div>
  
  <div class="dialog-footer">
    <button onclick="resetSettings()">Reset to Defaults</button>
    <button onclick="saveSettings()">Save Changes</button>
  </div>
</dialog>

<button onclick="document.getElementById('settingsDialog').showModal()">
  Open Settings
</button>

<script>
function saveSettings() {
  const dialog = document.getElementById('settingsDialog');
  const formData = new FormData(dialog);
  
  // Process settings
  for (let [key, value] of formData) {
    console.log(`Setting ${key}: ${value}`);
  }
  
  dialog.close();
}

function resetSettings() {
  const checkboxes = document.querySelectorAll('#settingsDialog input[type="checkbox"]');
  const selects = document.querySelectorAll('#settingsDialog select');
  
  checkboxes.forEach(checkbox => checkbox.checked = false);
  selects.forEach(select => select.value = 'medium');
  
  // Re-check default values
  document.querySelector('input[name="emailNotifications"]').checked = true;
}
</script>

<style>
#settingsDialog {
  border: none;
  border-radius: 12px;
  padding: 0;
  width: 90%;
  max-width: 500px;
  max-height: 80vh;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.dialog-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 24px;
  border-bottom: 1px solid #e9ecef;
  background: #f8f9fa;
  border-radius: 12px 12px 0 0;
}

.dialog-header h2 {
  margin: 0;
  color: #333;
}

.close-button {
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #666;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.close-button:hover {
  background: #e9ecef;
  color: #333;
}

.dialog-content {
  padding: 24px;
  max-height: 400px;
  overflow-y: auto;
}

.settings-section {
  margin-bottom: 32px;
}

.settings-section h3 {
  margin: 0 0 16px 0;
  color: #333;
  font-size: 1.2em;
  border-bottom: 1px solid #e9ecef;
  padding-bottom: 8px;
}

.setting {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
  padding: 8px 0;
}

.setting label {
  color: #555;
  font-weight: 500;
}

.setting input[type="checkbox"] {
  margin-right: 8px;
}

.setting select {
  padding: 6px 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  background: white;
}

.dialog-footer {
  padding: 20px 24px;
  border-top: 1px solid #e9ecef;
  background: #f8f9fa;
  border-radius: 0 0 12px 12px;
  display: flex;
  justify-content: flex-end;
  gap: 12px;
}

.dialog-footer button {
  padding: 10px 20px;
  border: 1px solid #007bff;
  border-radius: 6px;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.2s;
}

.dialog-footer button:first-child {
  background: white;
  color: #007bff;
}

.dialog-footer button:last-child {
  background: #007bff;
  color: white;
}

.dialog-footer button:hover {
  opacity: 0.9;
  transform: translateY(-1px);
}

#settingsDialog::backdrop {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
}
</style>
```

**Alert dialog with auto-close:**
```html
<dialog id="alertDialog">
  <div class="alert-content">
    <div class="alert-icon">⚠️</div>
    <div class="alert-text">
      <h3>Session Expiring</h3>
      <p>Your session will expire in 5 minutes due to inactivity.</p>
    </div>
  </div>
  <div class="alert-actions">
    <button onclick="extendSession()">Extend Session</button>
    <button onclick="document.getElementById('alertDialog').close()">Dismiss</button>
  </div>
</dialog>

<button onclick="showAlert()">Show Alert</button>

<script>
let autoCloseTimer;

function showAlert() {
  const dialog = document.getElementById('alertDialog');
  dialog.showModal();
  
  // Auto-close after 10 seconds
  autoCloseTimer = setTimeout(() => {
    dialog.close();
  }, 10000);
  
  dialog.addEventListener('close', () => {
    clearTimeout(autoCloseTimer);
  });
}

function extendSession() {
  clearTimeout(autoCloseTimer);
  document.getElementById('alertDialog').close();
  console.log('Session extended');
}
</script>

<style>
#alertDialog {
  border: none;
  border-radius: 12px;
  padding: 24px;
  max-width: 400px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
  animation: slideIn 0.3s ease-out;
}

.alert-content {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  margin-bottom: 20px;
}

.alert-icon {
  font-size: 24px;
  flex-shrink: 0;
}

.alert-text h3 {
  margin: 0 0 8px 0;
  color: #333;
}

.alert-text p {
  margin: 0;
  color: #666;
  line-height: 1.5;
}

.alert-actions {
  display: flex;
  gap: 12px;
  justify-content: flex-end;
}

.alert-actions button {
  padding: 10px 20px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background: white;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.2s;
}

.alert-actions button:first-child {
  background: #007bff;
  color: white;
  border-color: #007bff;
}

.alert-actions button:hover {
  transform: translateY(-1px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

#alertDialog::backdrop {
  background: rgba(0, 0, 0, 0.4);
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-20px) scale(0.9);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
</style>
```

**Login form dialog:**
```html
<dialog id="loginDialog">
  <form method="dialog" class="login-form">
    <div class="form-header">
      <h2>Welcome Back</h2>
      <p>Please sign in to your account</p>
    </div>
    
    <div class="form-group">
      <label for="email">Email Address</label>
      <input type="email" id="email" name="email" required placeholder="Enter your email">
    </div>
    
    <div class="form-group">
      <label for="password">Password</label>
      <input type="password" id="password" name="password" required placeholder="Enter your password">
    </div>
    
    <div class="form-options">
      <label>
        <input type="checkbox" name="remember"> Remember me
      </label>
      <a href="#forgot-password">Forgot password?</a>
    </div>
    
    <button type="submit" class="login-button">Sign In</button>
    
    <div class="form-footer">
      <p>Don't have an account? <a href="#signup">Sign up</a></p>
    </div>
  </form>
</dialog>

<button onclick="document.getElementById('loginDialog').showModal()">
  Sign In
</button>

<script>
const loginDialog = document.getElementById('loginDialog');

loginDialog.addEventListener('close', () => {
  if (loginDialog.returnValue !== '') {
    const formData = new FormData(loginDialog.querySelector('form'));
    const email = formData.get('email');
    console.log(`User logged in: ${email}`);
    // Handle login logic
  }
});

// Prevent dialog close on backdrop click for login form
loginDialog.addEventListener('click', (event) => {
  if (event.target === loginDialog) {
    event.preventDefault();
  }
});
</script>

<style>
#loginDialog {
  border: none;
  border-radius: 16px;
  padding: 0;
  width: 90%;
  max-width: 400px;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.25);
  animation: scaleIn 0.3s ease-out;
}

.login-form {
  padding: 32px;
}

.form-header {
  text-align: center;
  margin-bottom: 32px;
}

.form-header h2 {
  margin: 0 0 8px 0;
  color: #333;
  font-size: 1.8em;
}

.form-header p {
  margin: 0;
  color: #666;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 6px;
  color: #333;
  font-weight: 500;
}

.form-group input {
  width: 100%;
  padding: 12px 16px;
  border: 2px solid #e9ecef;
  border-radius: 8px;
  font-size: 16px;
  transition: border-color 0.2s;
  box-sizing: border-box;
}

.form-group input:focus {
  outline: none;
  border-color: #007bff;
}

.form-options {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
  font-size: 14px;
}

.form-options label {
  display: flex;
  align-items: center;
  gap: 6px;
  color: #666;
}

.form-options a {
  color: #007bff;
  text-decoration: none;
}

.form-options a:hover {
  text-decoration: underline;
}

.login-button {
  width: 100%;
  padding: 14px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.login-button:hover {
  background: #0056b3;
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(0, 123, 255, 0.3);
}

.form-footer {
  text-align: center;
  margin-top: 24px;
  padding-top: 20px;
  border-top: 1px solid #e9ecef;
  color: #666;
}

.form-footer a {
  color: #007bff;
  text-decoration: none;
  font-weight: 500;
}

.form-footer a:hover {
  text-decoration: underline;
}

#loginDialog::backdrop {
  background: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(8px);
}

@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
</style>
```

**Image gallery lightbox:**
```html
<dialog id="lightboxDialog">
  <div class="lightbox-container">
    <button class="lightbox-close" onclick="document.getElementById('lightboxDialog').close()">
      ×
    </button>
    <button class="lightbox-nav lightbox-prev" onclick="prevImage()">‹</button>
    
    <div class="lightbox-content">
      <img id="lightboxImage" src="" alt="">
      <div class="lightbox-caption">
        <h3 id="imageTitle">Image Title</h3>
        <p id="imageDescription">Image description</p>
      </div>
    </div>
    
    <button class="lightbox-nav lightbox-next" onclick="nextImage()">›</button>
  </div>
</dialog>

<div class="gallery">
  <div class="gallery-item" onclick="openLightbox(0)">
    <img src="image1-thumb.jpg" alt="Mountain landscape" data-full="image1-full.jpg"
         data-title="Mountain Landscape" data-desc="Beautiful mountain view at sunrise">
  </div>
  <div class="gallery-item" onclick="openLightbox(1)">
    <img src="image2-thumb.jpg" alt="Ocean waves" data-full="image2-full.jpg"
         data-title="Ocean Waves" data-desc="Powerful waves crashing on the shore">
  </div>
  <div class="gallery-item" onclick="openLightbox(2)">
    <img src="image3-thumb.jpg" alt="Forest path" data-full="image3-full.jpg"
         data-title="Forest Path" data-desc="Sunlight filtering through forest trees">
  </div>
</div>

<script>
const images = [
  {
    full: 'image1-full.jpg',
    title: 'Mountain Landscape',
    desc: 'Beautiful mountain view at sunrise'
  },
  {
    full: 'image2-full.jpg',
    title: 'Ocean Waves',
    desc: 'Powerful waves crashing on the shore'
  },
  {
    full: 'image3-full.jpg',
    title: 'Forest Path',
    desc: 'Sunlight filtering through forest trees'
  }
];

let currentImageIndex = 0;

function openLightbox(index) {
  currentImageIndex = index;
  showImage();
  document.getElementById('lightboxDialog').showModal();
}

function showImage() {
  const image = images[currentImageIndex];
  document.getElementById('lightboxImage').src = image.full;
  document.getElementById('imageTitle').textContent = image.title;
  document.getElementById('imageDescription').textContent = image.desc;
}

function nextImage() {
  currentImageIndex = (currentImageIndex + 1) % images.length;
  showImage();
}

function prevImage() {
  currentImageIndex = (currentImageIndex - 1 + images.length) % images.length;
  showImage();
}

// Keyboard navigation
document.addEventListener('keydown', (event) => {
  const dialog = document.getElementById('lightboxDialog');
  if (dialog.open) {
    if (event.key === 'ArrowRight') nextImage();
    if (event.key === 'ArrowLeft') prevImage();
    if (event.key === 'Escape') dialog.close();
  }
});
</script>

<style>
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 16px;
  margin: 20px 0;
}

.gallery-item {
  cursor: pointer;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s;
}

.gallery-item:hover {
  transform: scale(1.05);
}

.gallery-item img {
  width: 100%;
  height: 150px;
  object-fit: cover;
}

#lightboxDialog {
  border: none;
  padding: 0;
  background: transparent;
  max-width: none;
  max-height: none;
  width: 100vw;
  height: 100vh;
}

.lightbox-container {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.9);
}

.lightbox-close {
  position: absolute;
  top: 20px;
  right: 20px;
  background: rgba(255, 255, 255, 0.2);
  border: none;
  color: white;
  font-size: 24px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  z-index: 10;
  backdrop-filter: blur(10px);
}

.lightbox-close:hover {
  background: rgba(255, 255, 255, 0.3);
}

.lightbox-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.2);
  border: none;
  color: white;
  font-size: 32px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
  backdrop-filter: blur(10px);
  z-index: 10;
}

.lightbox-prev {
  left: 20px;
}

.lightbox-next {
  right: 20px;
}

.lightbox-nav:hover {
  background: rgba(255, 255, 255, 0.3);
}

.lightbox-content {
  max-width: 90%;
  max-height: 90%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.lightbox-content img {
  max-width: 100%;
  max-height: calc(90vh - 100px);
  object-fit: contain;
}

.lightbox-caption {
  color: white;
  text-align: center;
  margin-top: 20px;
  max-width: 600px;
}

.lightbox-caption h3 {
  margin: 0 0 8px 0;
  font-size: 1.5em;
}

.lightbox-caption p {
  margin: 0;
  opacity: 0.8;
}

#lightboxDialog::backdrop {
  background: transparent;
}
</style>
```

**Accessible dialog with focus management:**
```html
<dialog id="accessibleDialog" aria-labelledby="dialogTitle" aria-describedby="dialogDesc">
  <div class="dialog-container">
    <h2 id="dialogTitle">Accessibility Settings</h2>
    <p id="dialogDesc">Customize the accessibility features for your experience.</p>
    
    <div class="settings-grid">
      <div class="setting-item">
        <label for="fontSize">Font Size</label>
        <select id="fontSize">
          <option value="small">Small</option>
          <option value="medium" selected>Medium</option>
          <option value="large">Large</option>
          <option value="x-large">Extra Large</option>
        </select>
      </div>
      
      <div class="setting-item">
        <label for="contrast">Color Contrast</label>
        <select id="contrast">
          <option value="normal">Normal</option>
          <option value="high">High Contrast</option>
          <option value="inverted">Inverted</option>
        </select>
      </div>
      
      <div class="setting-item">
        <label>
          <input type="checkbox" id="reducedMotion"> Reduced Motion
        </label>
      </div>
      
      <div class="setting-item">
        <label>
          <input type="checkbox" id="screenReader"> Screen Reader Optimized
        </label>
      </div>
    </div>
    
    <div class="dialog-actions">
      <button onclick="resetAccessibility()" aria-label="Reset to default accessibility settings">
        Reset
      </button>
      <button onclick="applyAccessibility()" class="primary">
        Apply Settings
      </button>
    </div>
  </div>
</dialog>

<button onclick="openAccessibleDialog()" aria-haspopup="dialog">
  Open Accessibility Settings
</button>

<script>
let previousActiveElement;

function openAccessibleDialog() {
  const dialog = document.getElementById('accessibleDialog');
  previousActiveElement = document.activeElement;
  
  dialog.showModal();
  
  // Focus first interactive element
  dialog.querySelector('select, button, input').focus();
}

function closeAccessibleDialog() {
  const dialog = document.getElementById('accessibleDialog');
  dialog.close();
  
  // Restore focus to previous element
  if (previousActiveElement) {
    previousActiveElement.focus();
  }
}

function resetAccessibility() {
  document.getElementById('fontSize').value = 'medium';
  document.getElementById('contrast').value = 'normal';
  document.getElementById('reducedMotion').checked = false;
  document.getElementById('screenReader').checked = false;
}

function applyAccessibility() {
  const settings = {
    fontSize: document.getElementById('fontSize').value,
    contrast: document.getElementById('contrast').value,
    reducedMotion: document.getElementById('reducedMotion').checked,
    screenReader: document.getElementById('screenReader').checked
  };
  
  console.log('Applied accessibility settings:', settings);
  closeAccessibleDialog();
  
  // Show confirmation
  alert('Accessibility settings applied successfully!');
}

// Close on Escape key
document.getElementById('accessibleDialog').addEventListener('keydown', (event) => {
  if (event.key === 'Escape') {
    closeAccessibleDialog();
  }
});

// Trap focus inside dialog
document.getElementById('accessibleDialog').addEventListener('keydown', (event) => {
  if (event.key !== 'Tab') return;
  
  const dialog = document.getElementById('accessibleDialog');
  const focusableElements = dialog.querySelectorAll('button, input, select, textarea, [href]');
  const firstElement = focusableElements[0];
  const lastElement = focusableElements[focusableElements.length - 1];
  
  if (event.shiftKey) {
    if (document.activeElement === firstElement) {
      lastElement.focus();
      event.preventDefault();
    }
  } else {
    if (document.activeElement === lastElement) {
      firstElement.focus();
      event.preventDefault();
    }
  }
});
</script>

<style>
#accessibleDialog {
  border: none;
  border-radius: 12px;
  padding: 0;
  max-width: 500px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.dialog-container {
  padding: 24px;
}

#accessibleDialog h2 {
  margin: 0 0 8px 0;
  color: #333;
  font-size: 1.5em;
}

#accessibleDialog p {
  margin: 0 0 24px 0;
  color: #666;
}

.settings-grid {
  display: grid;
  gap: 20px;
  margin-bottom: 24px;
}

.setting-item {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.setting-item label {
  font-weight: 500;
  color: #333;
}

.setting-item select {
  padding: 8px 12px;
  border: 2px solid #e9ecef;
  border-radius: 6px;
  font-size: 14px;
}

.setting-item select:focus {
  outline: none;
  border-color: #007bff;
}

.setting-item input[type="checkbox"] {
  margin-right: 8px;
}

.dialog-actions {
  display: flex;
  gap: 12px;
  justify-content: flex-end;
}

.dialog-actions button {
  padding: 10px 20px;
  border: 2px solid #007bff;
  border-radius: 6px;
  background: white;
  color: #007bff;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.2s;
}

.dialog-actions button.primary {
  background: #007bff;
  color: white;
}

.dialog-actions button:hover {
  transform: translateY(-1px);
  box-shadow: 0 2px 8px rgba(0, 123, 255, 0.3);
}

#accessibleDialog::backdrop {
  background: rgba(0, 0, 0, 0.5);
}

/* High contrast support */
@media (prefers-contrast: high) {
  #accessibleDialog {
    border: 3px solid #000;
  }
  
  .setting-item select {
    border-width: 3px;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  #accessibleDialog {
    animation: none;
  }
  
  .dialog-actions button {
    transition: none;
  }
}
</style>
```

---

## Notes

* **Browser support**: 
  - Modern browsers have good support (Chrome, Firefox, Safari, Edge)
  - Some older browsers may require polyfills
  - Check current support on Can I Use
* **Accessibility benefits**:
  - Native focus management and trapping
  - Automatic ARIA role assignment
  - Backdrop prevents background interaction
  - Escape key support built-in
* **Methods and properties**:
  - `showModal()`: Opens as modal dialog
  - `show()`: Opens as non-modal dialog
  - `close()`: Closes the dialog
  - `returnValue`: Gets/sets return value
  - `open`: Reflects the open state
* **Common issues**:
  - Forgetting to call `showModal()` instead of just setting `open` attribute
  - Not handling focus management properly in complex dialogs
  - Missing proper fallback for unsupported browsers
  - Incorrect use of `method="dialog"` in forms
* **Best practices**:
  - Always provide a way to close the dialog
  - Use `showModal()` for modal dialogs that require user interaction
  - Trap focus inside modal dialogs for accessibility
  - Provide proper ARIA labels and descriptions
  - Consider mobile responsiveness and touch interactions
* **Polyfill considerations**:
  - Use the `<dialog>` polyfill for older browsers
  - Test fallback behavior thoroughly
  - Consider progressive enhancement
* **Performance**:
  - Native dialogs have better performance than JavaScript-based modals
  - Consider lazy loading dialog content if heavy
  - Avoid complex animations that may cause jank
* **Security**:
  - No additional security considerations beyond normal HTML
  - Be cautious with user-generated content in dialogs
* **Mobile considerations**:
  - Ensure dialogs are responsive and touch-friendly
  - Consider viewport height issues on mobile
  - Test keyboard dismissal on mobile devices

---
