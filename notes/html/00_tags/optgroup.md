# `<optgroup>`

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

The `<optgroup>` element creates a grouping of options within a `<select>` element, providing a way to categorize and organize related options under descriptive labels. It enhances usability by visually and semantically grouping similar choices, making long option lists more navigable and understandable for users.

---

## Syntax and Variants

+ **Standard syntax**: `<optgroup>...</optgroup>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps one or more `<option>` elements
+ **No self-closing variant**: Must contain option elements
+ **Grouping element**: Serves as a parent for related options

---

## Attributes

+ **Core attributes**:
  - `label` (required): The text label for the option group
  - `disabled` (optional): Disables all options in the group (boolean)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**: Zero or more `<option>` elements
+ **Required children**: At least one `<option>` for meaningful grouping
+ **Nesting restriction**: Cannot contain other `<optgroup>` elements
+ **Mixed content**: Cannot contain text directly, only `<option>` elements

---

## Context

+ **Required parent**: Must be a direct child of `<select>` element
+ **Sibling relationships**:
  - Can be mixed with standalone `<option>` elements
  - Multiple `<optgroup>` elements can exist within one `<select>`
  - Order determines display order in dropdown
+ **Group hierarchy**: Creates a two-level hierarchy within the select

---

## Behavior and Semantics

+ **Default display**: No independent visual representation
+ **Default styling**:
  - Group labels typically appear bold or emphasized
  - Often indented or visually separated from options
  - Browser-dependent appearance (usually non-selectable header)
  - Disabled groups appear grayed out
+ **Interactive behavior**:
  - Group labels are not selectable
  - Options within groups behave normally
  - Keyboard navigation skips over group labels
  - Disabled groups make all contained options unavailable
+ **Semantic meaning**:
  - Represents a logical grouping of related options
  - Screen readers announce group labels before reading contained options
  - Provides hierarchical organization for complex option sets
+ **Accessibility**: Helps screen reader users understand option categories and relationships

---

## Examples

**Basic optgroup for categorizing options:**
```html
<label for="car-select">Choose a Car:</label>
<select id="car-select" name="car">
  <optgroup label="Japanese Brands">
    <option value="toyota">Toyota</option>
    <option value="honda">Honda</option>
    <option value="nissan">Nissan</option>
  </optgroup>
  <optgroup label="American Brands">
    <option value="ford">Ford</option>
    <option value="chevrolet">Chevrolet</option>
    <option value="dodge">Dodge</option>
  </optgroup>
  <optgroup label="European Brands">
    <option value="bmw">BMW</option>
    <option value="mercedes">Mercedes-Benz</option>
    <option value="audi">Audi</option>
  </optgroup>
</select>
```

**Mixed optgroups and standalone options:**
```html
<label for="food-select">Food Preferences:</label>
<select id="food-select" name="food">
  <option value="">Select a food category</option>
  
  <optgroup label="Fruits">
    <option value="apple">Apple</option>
    <option value="banana">Banana</option>
    <option value="orange">Orange</option>
  </optgroup>
  
  <optgroup label="Vegetables">
    <option value="carrot">Carrot</option>
    <option value="broccoli">Broccoli</option>
    <option value="spinach">Spinach</option>
  </optgroup>
  
  <option value="other">Other (please specify)</option>
</select>
```

**Disabled optgroup:**
```html
<label for="subscription-select">Subscription Plan:</label>
<select id="subscription-select" name="subscription">
  <option value="">Choose a plan</option>
  
  <optgroup label="Available Plans">
    <option value="free">Free Plan</option>
    <option value="basic">Basic Plan - $9.99/month</option>
    <option value="premium">Premium Plan - $19.99/month</option>
  </optgroup>
  
  <optgroup label="Coming Soon" disabled>
    <option value="enterprise">Enterprise Plan</option>
    <option value="custom">Custom Plan</option>
  </optgroup>
</select>
```

**Optgroup with styled options:**
```html
<label for="department-select">Department:</label>
<select id="department-select" name="department">
  <option value="">Select a department</option>
  
  <optgroup label="Engineering" class="engineering-group">
    <option value="frontend">Frontend Development</option>
    <option value="backend">Backend Development</option>
    <option value="devops">DevOps</option>
  </optgroup>
  
  <optgroup label="Design" class="design-group">
    <option value="ui">UI Design</option>
    <option value="ux">UX Design</option>
    <option value="graphic">Graphic Design</option>
  </optgroup>
  
  <optgroup label="Business" class="business-group">
    <option value="marketing">Marketing</option>
    <option value="sales">Sales</option>
    <option value="finance">Finance</option>
  </optgroup>
</select>

<style>
/* Note: Styling optgroups has limited browser support */
.engineering-group { color: #3498db; }
.design-group { color: #9b59b6; }
.business-group { color: #2ecc71; }

/* Better approach: use data attributes and JavaScript for advanced styling */
</style>
```

**Nested categorization with detailed labels:**
```html
<label for="software-select">Software Category:</label>
<select id="software-select" name="software">
  <optgroup label="Productivity Software">
    <option value="ms-office">Microsoft Office Suite</option>
    <option value="google-workspace">Google Workspace</option>
    <option value="libreoffice">LibreOffice</option>
  </optgroup>
  
  <optgroup label="Creative Tools">
    <option value="adobe-creative-cloud">Adobe Creative Cloud</option>
    <option value="figma">Figma</option>
    <option value="sketch">Sketch</option>
  </optgroup>
  
  <optgroup label="Development Environments">
    <option value="vscode">Visual Studio Code</option>
    <option value="intellij">IntelliJ IDEA</option>
    <option value="sublime">Sublime Text</option>
  </optgroup>
  
  <optgroup label="Communication Tools">
    <option value="slack">Slack</option>
    <option value="teams">Microsoft Teams</option>
    <option value="zoom">Zoom</option>
  </optgroup>
</select>
```

**Optgroup with international content:**
```html
<label for="language-select">Programming Language:</label>
<select id="language-select" name="language">
  <optgroup label="Web Development">
    <option value="javascript">JavaScript</option>
    <option value="typescript">TypeScript</option>
    <option value="html-css">HTML/CSS</option>
  </optgroup>
  
  <optgroup label="Backend Languages">
    <option value="python">Python</option>
    <option value="java">Java</option>
    <option value="csharp">C#</option>
    <option value="php">PHP</option>
  </optgroup>
  
  <optgroup label="Mobile Development">
    <option value="swift">Swift (iOS)</option>
    <option value="kotlin">Kotlin (Android)</option>
    <option value="react-native">React Native</option>
  </optgroup>
  
  <optgroup label="Systems Programming">
    <option value="c">C</option>
    <option value="cpp">C++</option>
    <option value="rust">Rust</option>
    <option value="go">Go</option>
  </optgroup>
</select>
```

**Dynamic optgroups with JavaScript:**
```html
<label for="dynamic-groups">Product Categories:</label>
<select id="dynamic-groups" name="category"></select>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const categories = {
    'Electronics': ['Smartphones', 'Laptops', 'Tablets', 'Accessories'],
    'Home & Garden': ['Furniture', 'Kitchen', 'Decor', 'Gardening'],
    'Clothing': ['Men', 'Women', 'Children', 'Accessories'],
    'Sports': ['Fitness', 'Outdoor', 'Team Sports', 'Water Sports']
  };
  
  const select = document.getElementById('dynamic-groups');
  
  // Add default option
  const defaultOption = document.createElement('option');
  defaultOption.value = "";
  defaultOption.textContent = "Select a category";
  select.appendChild(defaultOption);
  
  // Create optgroups and options
  Object.entries(categories).forEach(([groupName, items]) => {
    const optgroup = document.createElement('optgroup');
    optgroup.label = groupName;
    
    items.forEach(item => {
      const option = document.createElement('option');
      option.value = item.toLowerCase().replace(/\s+/g, '-');
      option.textContent = item;
      optgroup.appendChild(option);
    });
    
    select.appendChild(optgroup);
  });
});
</script>
```

**Accessible optgroups with ARIA:**
```html
<label for="accessible-groups">Notification Settings:</label>
<select id="accessible-groups" name="notifications" aria-describedby="groups-description">
  <optgroup label="Email Notifications" aria-label="Email notification options">
    <option value="email-all">All Email Notifications</option>
    <option value="email-important">Important Emails Only</option>
    <option value="email-none">No Email Notifications</option>
  </optgroup>
  
  <optgroup label="Push Notifications" aria-label="Push notification options">
    <option value="push-all">All Push Notifications</option>
    <option value="push-mentions">Mentions Only</option>
    <option value="push-none">No Push Notifications</option>
  </optgroup>
  
  <optgroup label="SMS Notifications" aria-label="SMS notification options" disabled>
    <option value="sms-important">Important SMS Alerts</option>
    <option value="sms-none">No SMS Notifications</option>
  </optgroup>
</select>

<div id="groups-description" class="visually-hidden">
  Categorized notification settings with email, push, and SMS options
</div>
```

**Optgroup with data attributes for enhanced functionality:**
```html
<label for="enhanced-groups">Service Plans:</label>
<select id="enhanced-groups" name="service_plan">
  <optgroup label="Basic Plans" data-tier="basic" data-popular="false">
    <option value="basic-free" data-price="0" data-features="limited">Free Plan</option>
    <option value="basic-starter" data-price="5" data-features="essential">Starter - $5/month</option>
  </optgroup>
  
  <optgroup label="Professional Plans" data-tier="professional" data-popular="true">
    <option value="pro-standard" data-price="15" data-features="standard">Standard - $15/month</option>
    <option value="pro-plus" data-price="25" data-features="premium">Plus - $25/month</option>
  </optgroup>
  
  <optgroup label="Enterprise Plans" data-tier="enterprise" data-popular="false">
    <option value="ent-business" data-price="50" data-features="business">Business - $50/month</option>
    <option value="ent-custom" data-price="custom" data-features="custom">Custom - Contact Sales</option>
  </optgroup>
</select>

<script>
document.getElementById('enhanced-groups').addEventListener('change', function() {
  const selectedOption = this.options[this.selectedIndex];
  const parentGroup = selectedOption.parentElement;
  
  const tier = parentGroup.getAttribute('data-tier');
  const isPopular = parentGroup.getAttribute('data-popular') === 'true';
  const price = selectedOption.getAttribute('data-price');
  const features = selectedOption.getAttribute('data-features');
  
  console.log(`Tier: ${tier}, Popular: ${isPopular}, Price: $${price}, Features: ${features}`);
});
</script>
```

**Optgroup in a multi-select scenario:**
```html
<label for="multi-group-select">Select Your Interests:</label>
<select id="multi-group-select" name="interests" multiple size="8">
  <optgroup label="Technology">
    <option value="web-dev">Web Development</option>
    <option value="mobile-dev">Mobile Development</option>
    <option value="ai-ml">Artificial Intelligence & ML</option>
    <option value="cloud-computing">Cloud Computing</option>
  </optgroup>
  
  <optgroup label="Business">
    <option value="entrepreneurship">Entrepreneurship</option>
    <option value="marketing">Digital Marketing</option>
    <option value="finance">Personal Finance</option>
    <option value="leadership">Leadership</option>
  </optgroup>
  
  <optgroup label="Creative Arts">
    <option value="graphic-design">Graphic Design</option>
    <option value="photography">Photography</option>
    <option value="writing">Creative Writing</option>
    <option value="music">Music Production</option>
  </optgroup>
</select>
<small>Hold Ctrl/Cmd to select multiple options</small>
```

**Optgroup with custom styling attempt (limited support):**
```html
<label for="styled-groups">Styled Option Groups:</label>
<select id="styled-groups" name="styled_option">
  <optgroup label="Primary Colors" style="font-weight: bold; color: #333;">
    <option value="red" style="color: #e74c3c;">Red</option>
    <option value="blue" style="color: #3498db;">Blue</option>
    <option value="yellow" style="color: #f1c40f;">Yellow</option>
  </optgroup>
  
  <optgroup label="Secondary Colors" style="font-weight: bold; color: #666;">
    <option value="green" style="color: #27ae60;">Green</option>
    <option value="orange" style="color: #e67e22;">Orange</option>
    <option value="purple" style="color: #9b59b6;">Purple</option>
  </optgroup>
</select>

<style>
/* Note: Inline styles on optgroup and option have limited browser support */
/* For consistent styling, consider a custom select implementation */
</style>
```

**Optgroup for geographic organization:**
```html
<label for="location-select">Office Locations:</label>
<select id="location-select" name="location">
  <optgroup label="North America">
    <option value="nyc">New York City, USA</option>
    <option value="sf">San Francisco, USA</option>
    <option value="toronto">Toronto, Canada</option>
    <option value="mexico-city">Mexico City, Mexico</option>
  </optgroup>
  
  <optgroup label="Europe">
    <option value="london">London, UK</option>
    <option value="berlin">Berlin, Germany</option>
    <option value="paris">Paris, France</option>
    <option value="amsterdam">Amsterdam, Netherlands</option>
  </optgroup>
  
  <optgroup label="Asia Pacific">
    <option value="tokyo">Tokyo, Japan</option>
    <option value="singapore">Singapore</option>
    <option value="sydney">Sydney, Australia</option>
    <option value="bangalore">Bangalore, India</option>
  </optgroup>
  
  <optgroup label="Remote Options">
    <option value="remote-us">Remote (USA)</option>
    <option value="remote-eu">Remote (Europe)</option>
    <option value="remote-global">Remote (Global)</option>
  </optgroup>
</select>
```

---

## Notes

* **Label attribute requirement**: The `label` attribute is required for `<optgroup>` to be valid HTML
* **Accessibility benefits**:
  - Screen readers announce group labels, providing context for options
  - Helps users understand the categorization of available choices
  - Improves navigation through long option lists
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Forgetting the required `label` attribute
  - Nesting `<optgroup>` elements (not allowed)
  - Putting text content directly in `<optgroup>` (only `<option>` allowed)
  - Using overly long group labels that get truncated
  - Expecting consistent styling across browsers
* **Styling limitations**:
  - CSS styling of `<optgroup>` has very limited browser support
  - Group label appearance is largely browser-dependent
  - Consider custom select implementations for design requirements
* **Mobile considerations**:
  - Native optgroup rendering varies by mobile OS
  - Group labels may appear differently on touch interfaces
  - Test with various mobile devices for consistent UX
* **Performance**: 
  - Using optgroups doesn't significantly impact performance
  - Large numbers of groups with many options follow same performance rules as regular selects
* **Best practices**:
  - Use clear, concise labels for groups
  - Keep related options logically grouped
  - Consider alphabetical ordering within groups
  - Use disabled groups to show unavailable options clearly
  - Test with screen readers for accessibility

---
