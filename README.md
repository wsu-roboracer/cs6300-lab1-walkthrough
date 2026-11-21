# CS 6300 &middot; Lab 1 Walkthrough

A code stepper for **Lab 1 — Introduction to ROS 2** in CS 6300 Autonomous Racing at Weber
State University. It runs the node the student is about to write, one line at a time: the code
on the left with the executing line highlighted, the ROS graph and the message under
construction in the middle, and the value of every variable at that moment on the right.

Live: **https://wsu-roboracer.github.io/cs6300-lab1-walkthrough/**

Built to the same pattern as the CS 1400 and CS 2420 steppers, so a student moving between
courses does not have to learn a second interface.

## Why this repo exists

The stepper ships with the [course site](https://github.com/wsu-roboracer/cs6300-course-site)
as `docs/_static/steppers/lab1.html`, linked from the Lab 1 page. This repo is a standalone
public copy so it can be iterated on and reviewed at its own URL before the change lands in
the course site. The course site is the destination; this repo is the workbench.

The only difference between the two copies: the footer link to the Lab 1 page is a relative
path on the course site and an absolute URL here.

## How it is laid out

| Column | What it holds |
|--------|---------------|
| **The code** | The finished version of the skeleton, with the executing line highlighted and a yellow band under it carrying that line's live values. Every line is clickable. |
| **The graph, right now** | `/talker`, `/drive`, `/relay`, `/drive_relay` — drawn dim until the line that creates them has run, and orange while carrying a message. Under it, the `AckermannDriveStamped` being filled in field by field. |
| **What the program is holding** | Every variable in scope and what it contains at this line, with the one that just changed marked. |

The theory is **not** on the page. Click any line of code and a box opens under it with what
that line is for, the arithmetic or syntax behind it, and what breaks without it — tagged
`why`, `trap`, `syntax` or `note`. Nineteen lines across the five panes have one.

## The tabs

| Tab | Walks |
|-----|-------|
| 1 &middot; The package | `package.xml` and `setup.py` — the dependency and the two entry points |
| 2 &middot; talker.py | `__init__`, then three timer ticks through `publish_drive` |
| 3 &middot; relay.py | `__init__`, then two messages through `drive_callback` |
| 4 &middot; The launch file | `lab1_launch.py`, action by action, up to both nodes starting |
| 5 &middot; See the graph | The terminal session: build, source, launch, `topic echo`, `param set`, `rqt_graph` |
| 6 &middot; What is graded | `check_lab1.py`'s own table, check by check, with what each one actually does |

The **Parameters** buttons switch the values the walk runs with. The third one,
*then param set v = 4.0*, changes the parameter mid-run — which is the only way to see why
`get_parameter` belongs in the callback and not in `__init__`.

## Controls

| Control | Action |
|---------|--------|
| **Tabs** | Switch which code is being walked |
| **Parameters** | Re-run the walk with different `v` and `d` |
| **&laquo; First** / **Last &raquo;** | Jump to the start or the end |
| **&lsaquo; Prev** / **Next &rsaquo;** | One line at a time |
| **&#9654; Play** | Auto-advance |
| **Click a line** | Open its popup; click again to close |
| **Click a rail entry** | Expand what that stretch of the walk is about |

Arrow keys step, space plays, Home and End jump to the ends. `#talker`, `#relay`, `#launch`,
`#cli` and `#graded` open a tab directly, so a Canvas page or a slide can link to one walk.

## Self-check

The page checks itself on load and prints the result at the bottom. The walks are generated
rather than typed, so the invariants are worth asserting: every step lands on a line that
exists, every step belongs to a rail entry, all nineteen line popups quote the line they are
filed under, the relay shows exactly 3x its input everywhere, and the graded table adds up to
the 75 points `check_lab1.py` actually scores. A red line at the bottom means a change broke
one of those.

## Files

```
cs6300-lab1-walkthrough/
├── index.html    # Everything: layout, CSS, code panes, line popups, walk builders
└── README.md
```

No build step, no dependencies. Open `index.html` in any modern browser.

To edit a walk, find its `build*` function — a step is one object with the line it executes,
the sentence for it, the live values, and the variables in scope. To edit the theory, find the
`info(...)` call for that line. Line numbers are looked up by text through `L(key, needle)`,
never typed in, so adding a line to a pane does not shift anything.

## Deploying

GitHub Pages serves the `main` branch root. Push to `main` and the live URL updates within
about a minute. No CI workflow needed.

## Embedding in Canvas

The layout wants width — it is three columns on a projector and stacks below about 1250px.

```html
<iframe
  src="https://wsu-roboracer.github.io/cs6300-lab1-walkthrough/"
  width="100%"
  height="900"
  frameborder="0">
</iframe>
```

## License

Course teaching material &mdash; free to use and adapt for educational purposes.
