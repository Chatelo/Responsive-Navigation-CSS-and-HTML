# CSS Documentation for Responsive Navigation Bar

## Basic Reset
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
- `*` selects all elements on the page
- `margin: 0` removes all outer spacing around elements
- `padding: 0` removes all inner spacing in elements
- `box-sizing: border-box` makes elements include padding in their total width/height

## Navigation Bar Container
```css
.navbar {
    height: 60px;              /* Sets fixed height */
    width: 100%;              /* Takes full width of parent */
    background: #333;         /* Dark gray background */
    padding: 0 16px;         /* Adds horizontal padding (top/bottom 0, left/right 16px) */
    display: flex;           /* Enables flexible layout */
    align-items: center;     /* Centers items vertically */
    justify-content: space-between;  /* Spreads items apart horizontally */
    position: relative;      /* For positioning dropdown menu */
}
```

## Brand Name Styling
```css
.brand-name {
    color: white;           /* White text color */
    font-size: 24px;       /* Text size */
}
```

## Navigation Links Container
```css
.nav-links {
    display: flex;         /* Makes items horizontal */
    list-style: none;     /* Removes bullet points */
    gap: 32px;           /* Space between nav items */
}

.nav-links a {
    color: white;         /* White text for links */
    text-decoration: none; /* Removes underline from links */
    font-size: 16px;      /* Text size */
    transition: color 0.3s ease; /* Smooth color change on hover */
}

.nav-links a:hover {
    color: #ddd;          /* Light gray on hover */
}
```

## Hamburger Menu (Mobile Toggle)
```css
.nav-toggle {
    display: none;        /* Hides checkbox */
}

.nav-toggle-label {
    display: none;        /* Hidden by default (shows in mobile) */
    flex-direction: column; /* Stacks spans vertically */
    gap: 5px;            /* Space between lines */
    cursor: pointer;      /* Hand cursor on hover */
}

.nav-toggle-label span {
    width: 25px;         /* Width of each line */
    height: 3px;         /* Thickness of each line */
    background: white;    /* White color for lines */
    transition: transform 0.3s ease; /* Smooth animation for menu icon */
}
```

## Mobile Responsive Design
```css
@media screen and (max-width: 768px) {
    /* Styles that apply only on screens smaller than 768px */

    .brand-name {
        display: none;    /* Hides brand name on mobile */
    }

    .nav-toggle-label {
        display: flex;    /* Shows hamburger menu */
        z-index: 2;       /* Keeps menu icon above other elements */
        margin-left: auto; /* Pushes menu to the right */
    }

    /* Mobile Menu Dropdown */
    .nav-links {
        position: absolute;    /* Takes it out of normal flow */
        top: 60px;            /* Positions below navbar */
        right: 16px;          /* Aligns to right */
        width: 200px;         /* Fixed width for dropdown */
        background: #333;      /* Dark background */
        flex-direction: column; /* Stacks items vertically */
        gap: 0;               /* Removes gap between items */
        display: none;        /* Hidden by default */
        border-radius: 0 0 4px 4px; /* Rounded bottom corners */
        box-shadow: 0 2px 5px rgba(0,0,0,0.2); /* Subtle shadow */
    }

    /* Mobile Menu Items */
    .nav-links li {
        text-align: center;   /* Centers text */
        padding: 16px;        /* Space around items */
        border-top: 1px solid #444; /* Separator between items */
    }

    /* Last item in dropdown */
    .nav-links li:last-child {
        border-radius: 0 0 4px 4px; /* Rounds bottom corners */
    }

    /* Show menu when checkbox is checked */
    .nav-toggle:checked ~ .nav-links {
        display: flex;
    }

    /* Hamburger to X Animation */
    .nav-toggle:checked ~ .nav-toggle-label span:nth-child(1) {
        transform: rotate(45deg) translate(5px, 5px);
    }

    .nav-toggle:checked ~ .nav-toggle-label span:nth-child(2) {
        opacity: 0;
    }

    .nav-toggle:checked ~ .nav-toggle-label span:nth-child(3) {
        transform: rotate(-45deg) translate(7px, -7px);
    }
}
```

### Summary
This CSS creates a responsive navigation bar that:
1. Shows a full horizontal menu on desktop
2. Switches to a hamburger menu on mobile (below 768px)
3. Has smooth animations and transitions
4. Is fully accessible with keyboard navigation
