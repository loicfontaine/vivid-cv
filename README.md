# vivid-cv

A clean and modern Typst ATS friendly resume template based on [Basic Resume](https://github.com/stuxf/basic-typst-resume-template) with a bold header banner, contact icons, and a flexible two-column intro section.

![preview](/preview.png)

## Features

- **Bold header banner** with name, title, and contact row
- **Font Awesome icons** for contact information (optional toggle)
- **Circular-style layout for intro section (beside photo)**
- **Fully customizable colors** (header, name, headings, text, photo border)
- **Smart banner height estimation** based on contact items
- **Optional footer reference line pinned at the bottom**
- **Lightweight section helpers** for CV structure:
  - `work`
  - `edu`
  - `project`
  - `certificates`
  - `extracurriculars`

## Quick start

```typst
#import "@preview/vivid-cv:0.1.0": *

#show: resume.with(
  author: "Jane Doe",
  title: "Full-Stack Engineer",

  email: "jane@example.com",
  github: "janedoe",
  linkedin: "jane-doe",
  phone: "+1 234 567 890",
  location: "Zurich, Switzerland",
  personal-site: "janedoe.dev",

  about-title: "About me",
  about-beside: [
    Passionate engineer with 5+ years of experience
    building web applications from design to deployment.
  ],

  reference: "References available upon request",

  header-color: "#06332a",
  lang: "en",
)

== Work Experience

#work(
  title: "Senior Engineer",
  company: "Acme Corp",
  dates: dates-helper(start-date: "Jan 2022", end-date: "Present"),
  location: "Zurich, Switzerland",
)

- Led migration from monolith to microservices
```

## Parameters

### Identity & contact

| Parameter       | Type   | Default | Description                |
| --------------- | ------ | ------- | -------------------------- |
| `author`        | string | `""`    | Full name                  |
| `title`         | string | `""`    | Job title / tagline        |
| `pronouns`      | string | `""`    | Optional pronouns          |
| `location`      | string | `""`    | City, country              |
| `email`         | string | `""`    | Email                      |
| `phone`         | string | `""`    | Phone number               |
| `github`        | string | `""`    | GitHub username            |
| `linkedin`      | string | `""`    | LinkedIn username          |
| `personal-site` | string | `""`    | Website (without https://) |
| `orcid`         | string | `""`    | ORCID ID                   |

### Intro section

| Parameter      | Type    | Default      | Description                          |
| -------------- | ------- | ------------ | ------------------------------------ |
| `about-title`  | string  | `"About me"` | Section title (set `""` to hide)     |
| `about-beside` | content | `[]`         | Text displayed beside the photo      |
| `about-below`  | content | `[]`         | Optional full-width text below intro |

### Photo

| Parameter    | Type   | Default    | Description                |
| ------------ | ------ | ---------- | -------------------------- |
| `show-photo` | bool   | `true`     | Toggle photo column        |
| `photo`      | string | `"pp.jpg"` | Path to image              |
| `photo-size` | length | `120pt`    | Diameter of circular photo |

### Colors

| Parameter       | Type   | Default     | Description                 |
| --------------- | ------ | ----------- | --------------------------- |
| `header-color`  | string | `"#06332a"` | Banner background           |
| `name-color`    | string | `"#ffdf2b"` | Name color                  |
| `heading-color` | string | `"#ffdf2b"` | Section heading color       |
| `text-color`    | string | `"#303f3c"` | Body text color             |
| `photo-border`  | string | `"ffffff"`  | Photo border color (no `#`) |

### Typography & layout

| Parameter          | Type   | Default                 | Description               |
| ------------------ | ------ | ----------------------- | ------------------------- |
| `font`             | string | `"New Computer Modern"` | Font family               |
| `author-font-size` | length | `20pt`                  | Name size                 |
| `font-size`        | length | `10pt`                  | Body text size            |
| `paper`            | string | `"a4"`                  | Paper size                |
| `lang`             | string | `"en"`                  | Language (hyphenation)    |
| `icon`             | bool   | `true`                  | Enable Font Awesome icons |

### Footer

| Parameter                | Type          | Default | Description                   |
| ------------------------ | ------------- | ------- | ----------------------------- |
| `reference`              | string        | `""`    | Footer line (empty = hidden)  |
| `banner-height-override` | length / none | `none`  | Force banner height if needed |

## Section helpers

```typst
#work(title: "", company: "", dates: "", location: "")

#edu(institution: "", degree: "", dates: "", location: "", gpa: "", consistent: false)

#project(role: "", name: "", url: "", dates: "")

#certificates(name: "", issuer: "", url: "", date: "")

#extracurriculars(activity: "", dates: "")

#dates-helper(start-date: "Jan 2020", end-date: "Present")
```

## Tips

### Hide photo

```typst
show-photo: false
```

### Adjust banner height (rare cases)

If long contact items break layout:

```typst
banner-height-override: 110pt
```

### Multilingual support

```typst
lang: "fr",
about-title: "À propos",
```

## Credits

Uses:

- [Font Awesome Typst package](https://typst.app/universe/package/fontawesome/)
- Based on [Basic Resume](https://github.com/stuxf/basic-typst-resume-template) by stuxf

## License

MIT
