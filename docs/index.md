import os

# Update _config.yml for a wedding theme
config_content = """
title: John & Jane's Wedding
description: Celebrate our special day with us!
author: John and Jane
email: johnandjane@example.com
baseurl: ""
url: "https://yourusername.github.io"
theme: minima
plugins:
  - jekyll-feed
"""

# Create folders if they don't exist
folders = ["_layouts", "_includes", "_posts", "pages"]
for folder in folders:
    os.makedirs(folder, exist_ok=True)

# Write updated _config.yml
with open("_config.yml", "w") as f:
    f.write(config_content)

# Create a custom wedding layout
wedding_layout = """
<!DOCTYPE html>
<html>
  <head>
    <meta charset='utf-8'>
    <title>{{ page.title }}</title>
    <style>
      body { font-family: 'Georgia', serif; background-color: #fffaf0; color: #333; text-align: center; }
      header { background-color: #f8e8e8; padding: 20px; }
      h1 { color: #b03060; }
      .content { margin: 20px; }
    </style>
  </head>
  <body>
    <header>
      <h1>{{ site.title }}</h1>
      <p>{{ site.description }}</p>
    </header>
    <div class="content">
      {{ content }}
    </div>
  </body>
</html>
"""

with open("_layouts/wedding.html", "w") as f:
    f.write(wedding_layout)

# Create a wedding homepage
index_content = """
---
layout: wedding
title: Our Wedding
---

## Welcome to Our Wedding Website

We are so excited to celebrate our special day with you!

### Event Details
- **Date:** June 15, 2026
- **Location:** Rosewood Garden, Vancouver
- **Time:** 4:00 PM Ceremony, followed by Reception

Please RSVP and find more details on the following pages.
"""

with open("index.md", "w") as f:
    f.write(index_content)

# Create a sample event details page
event_page = """
---
layout: wedding
title: Event Details
permalink: /details/
---

### Ceremony
- Starts at 4:00 PM
- Location: Rosewood Garden

### Reception
- Dinner and dancing to follow
- Dress code: Semi-formal

We can't wait to see you there!
"""

with open("pages/details.md", "w") as f:
    f.write(event_page)

print("Wedding-themed Jekyll site customization files have been created.")
