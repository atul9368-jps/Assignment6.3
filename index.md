The HTML File (index.html)
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Overflow Practice</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header class="page-header">
        <h1>CSS Overflow Showcase</h1>
        <p>Testing how containers handle content that exceeds fixed height and width constraints.</p>
    </header>

    <main class="container">
        
        <!-- Test 1: overflow: visible -->
        <section class="overflow-box box-visible">
            <h2>1. overflow: visible (Default)</h2>
            <p>This text is long enough to overflow the fixed height of the box. Notice how the extra text spills out and overlaps elements below it because overflow is visible by default.</p>
        </section>

        <!-- Test 2: overflow: hidden -->
        <section class="overflow-box box-hidden">
            <h2>2. overflow: hidden</h2>
            <p>This text is long enough to overflow the fixed height of the box. With overflow set to hidden, any content that extends past the boundary is clipped and completely hidden from view.</p>
        </section>

        <!-- Test 3: overflow: scroll -->
        <section class="overflow-box box-scroll">
            <h2>3. overflow: scroll</h2>
            <p>This text is long enough to overflow the fixed height of the box. Setting overflow to scroll forces scrollbars to appear on the container regardless of whether the content actually needs scrolling.</p>
        </section>

        <!-- Test 4 & Steps 4-5: overflow: auto (Scrollable Content Box) -->
        <section class="overflow-box box-auto">
            <h2>4. overflow: auto (Recommended)</h2>
            <p>This text is long enough to overflow the fixed height of the box. Overflow auto intelligently adds scrollbars only when the content exceeds the box dimensions, keeping your layout clean and accessible.</p>
        </section>

    </main>

</body>
</html>
2. The CSS File (style.css)
CSS
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f8fafc;
    color: #334155;
    margin: 0;
    padding: 30px;
    line-height: 1.6;
}

.page-header {
    text-align: center;
    margin-bottom: 30px;
}

.container {
    max-width: 600px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

/* Base style for test boxes */
.overflow-box {
    background-color: #ffffff;
    border: 2px solid #cbd5e1;
    border-radius: 8px;
    padding: 15px;
    height: 120px; /* Step 1: Fixed height container */
}

.overflow-box h2 {
    font-size: 1.1rem;
    margin-top: 0;
    margin-bottom: 8px;
    color: #1e293b;
}

.overflow-box p {
    margin: 0;
    color: #64748b;
}

/* Step 3: Testing different overflow values */

/* 1. Visible */
.box-visible {
    overflow: visible; /* Content spills out of the bottom border */
}

/* 2. Hidden */
.box-hidden {
    overflow: hidden; /* Excess content is clipped and cut off */
}

/* 3. Scroll */
.box-scroll {
    overflow: scroll; /* Always displays both horizontal and vertical scrollbars */
}

/* 4 & 5. Auto (Fixed Layout Issue) */
.box-auto {
    overflow: auto; /* Displays scrollbars only when content exceeds 120px */
}
3. Summary of Overflow Values Tested
visible (Default): Content overflows its container boundaries and spills over neighboring layout sections.

hidden: Clips any overflowing content. While it prevents messy layout breaks, users cannot read the hidden text.

scroll: Forces scrollbars to be present at all times on the box, even if the content is short enough to fit easily.

auto: The best practice for scrollable text boxes. It automatically adds scrollbars only when content overflows the fixed height.

4. Fixing Layout Overflow Issues (Step 5 Notes)
The Problem: When building responsive cards or sidebars, fixed heights (height: Xpx) combined with dynamic user text often cause text to burst out of containers or overlap footers.

