---
# An instance of the Accomplishments widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: accomplishments

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 50

# Note: `&shy;` is used to add a 'soft' hyphen in a long heading.
title: 'Awards'
subtitle:

# Spacing for the widget.  Customize the section spacing.  Order is top, right, bottom, left. 
design:
  spacing:
    padding: ["0px", "0", "20px", "0"]
# Background
  background:
    # Name of image in `assets/media/`.
    image: background.jpg
    # Darken the image? Range 0-1 where 0 is transparent and 1 is opaque.
    image_darken: 0.6
    #  Options are `cover` (default), `contain`, or `actual` size.
    image_size: cover
    # Options include `left`, `center` (default), or `right`.
    image_position: center
    # Use a fun parallax-like fixed background effect on desktop? true/false
    image_parallax: true
    # Text color (true=light, false=dark, or remove for the dynamic theme color).
    text_color_light: true


# Date format
#   Refer to https://wowchemy.com/docs/customization/#date-format
date_format: Jan 2006

# Accomplishments.
#   Add/remove as many `item` blocks below as you like.
#   `title`, `organization`, and `date_start` are the required parameters.
#   Leave other parameters empty if not required.
#   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
item:
- certificate_url: 
  date_end: ""
  date_start: "2015-07-01"
  description: "[Jaga-Me](https://www.jaga-me.com) won 3rd prize at the [IMDA-MIT HackMed hackathon 2015](https://www.asianscientist.com/2015/08/features/mit-hacking-medicinesg-2015). Jaga-Me went on to win the [NTUC Income Future Starter Challenge](https://www.straitstimes.com/singapore/uber-of-home-care-app-bags-top-prize-in-100k-challenge/) and currently provides home nursing services and related healthcare services in Singapore."
  organization: Infocomm Media Development Authority-MIT
  # organization_url: https://www.coursera.org
  title: 3rd prize - IMDA-MIT Hacking Medicine@SG 2015
  url: ""
# - certificate_url: https://www.datacamp.com
#   date_end: "2020-12-21"
#   date_start: "2020-07-01"
#   description: ""
#   organization: DataCamp
#   organization_url: https://www.datacamp.com
#   title: 'Object-Oriented Programming in R'
#   url: ""

design:
  columns: '2' 
---
