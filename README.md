# CS 6300 &middot; Lab 1 Walkthrough

Interactive six-step walkthrough of **Lab 1 — Introduction to ROS 2** for CS 6300 Autonomous
Racing at Weber State University. It shows the ROS 2 graph growing as the student builds it,
in the order the lab is actually written.

Live: **https://wsu-roboracer.github.io/cs6300-lab1-walkthrough/**

## Why this repo exists

The walkthrough ships with the [course site](https://github.com/wsu-roboracer/cs6300-course-site)
as `docs/_static/steppers/lab1.html`, linked from the Lab 1 page. This repo is a standalone
public copy so it can be iterated on and reviewed on its own URL before the change lands in
the course site. Treat the course site as the destination and this repo as the workbench —
when a revision is ready, it goes back into `docs/_static/steppers/lab1.html` in a PR there.

The only difference between the two copies: the footer link to the Lab 1 page is a relative
path on the course site and an absolute URL here.

## The six steps

| Step | What it covers |
|------|----------------|
| 1 &middot; The package | `package.xml` dependency on `ackermann_msgs`, `setup.py` console entry points |
| 2 &middot; talker publishes | Publisher, timer, and the declared `v` / `d` parameters on `/drive` |
| 3 &middot; relay listens | The subscriber, and the graph closing into a chain |
| 4 &middot; The launch file | Bringing both nodes up together |
| 5 &middot; See the graph | `ros2 topic`, `ros2 node`, `rqt_graph` against what was just built |
| 6 &middot; What is graded | The checks the submission has to pass |

Each step pairs the instructions with an SVG of the graph at that moment, so only the nodes
and topics that exist yet are lit.

## Controls

| Control | Action |
|---------|--------|
| **Step tabs** | Jump straight to any step |
| **&laquo; First** / **Last &raquo;** | Jump to the start or the end |
| **&lsaquo; Prev** / **Next &rsaquo;** | One step at a time |
| **&#9654; Play** | Auto-advance through the steps |

Arrow keys step forward and back.

## Files

```
cs6300-lab1-walkthrough/
├── index.html    # Everything: layout, CSS, step content, SVG rendering
└── README.md
```

No build step, no dependencies. Open `index.html` in any modern browser. The step content
lives in the `STEPS` array near the top of the inline script — editing a step means editing
one object.

Light and dark are both supported: the palette follows `prefers-color-scheme`, with a
`data-theme` attribute override.

## Deploying

GitHub Pages serves the `main` branch root. Push to `main` and the live URL updates within
about a minute. No CI workflow needed.

## Embedding in Canvas

```html
<iframe
  src="https://wsu-roboracer.github.io/cs6300-lab1-walkthrough/"
  width="1040"
  height="860"
  frameborder="0"
  style="max-width: 100%;">
</iframe>
```

## License

Course teaching material &mdash; free to use and adapt for educational purposes.
