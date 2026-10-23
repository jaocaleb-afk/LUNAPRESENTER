# LunaPresenter — Product Description & Feature Specification

## 1. What LunaPresenter is

**LunaPresenter is an HTML-first, browser-based presentation and live-production application for churches, worship teams, and event operators.** It is intended to help a team prepare an entire service, manage lyrics and media, control what appears on audience displays, and give speakers and musicians the information they need on stage—all from one coherent workspace.

LunaPresenter takes inspiration from the breadth of live presentation tools such as ProPresenter, while developing its own identity, interface, workflows, and implementation. The goal is not merely to display slides. The goal is to provide a practical command center for the visual side of a church service or live event.

## 2. Core technical principle: built in HTML

LunaPresenter should be built using **web technologies: HTML, CSS, and JavaScript**. The user interface and primary application experience should remain in HTML rather than being rewritten as a native desktop application.

### What this means

- **HTML** provides the application structure, panels, editors, controls, service rundown, slide surfaces, and output pages.
- **CSS** provides the design system, responsive layouts, slide styling, animations, themes, and screen-specific layouts.
- **JavaScript** provides the application behavior: editing, navigation, timers, media controls, output state, keyboard shortcuts, import/export, and interactions.
- The initial application should run in a modern browser and be straightforward to open, test, and develop.
- Keep the early product as self-contained as practical. Prefer a working HTML/CSS/JavaScript implementation and simple browser storage before introducing infrastructure that is not yet needed.
- Keep code organized and maintainable even when the application is delivered as a single HTML file. If the project later separates JavaScript, CSS, assets, or modules into multiple files, it should remain a web application built with the same technologies.
- Use browser capabilities such as local storage, file import/export, media playback, and separate browser windows where appropriate.
- Design for graceful limitations: browser-only code cannot automatically provide every operating-system-level display, professional video I/O, MIDI/DMX, hardware control, or network-service integration. Those capabilities must be investigated individually and may require supported browser APIs, permissions, companion services, or a future bridge. Do not pretend a browser can access hardware that it cannot.
- A backend is **not a prerequisite for the initial prototype**. Future sync, user accounts, cloud libraries, team collaboration, remote control, and integrations can be added later if needed without changing the HTML-first product identity.

**Architecture rule:** do not introduce a backend, framework, build system, or native wrapper merely for its own sake. Propose additional complexity only when there is a clear user need and explain the trade-off before adopting it.

## 3. Product vision

Create a polished, dependable, operator-first workspace that lets a volunteer or experienced production operator move from service preparation to live execution with confidence. The interface should remain readable and calm under pressure, make the live state unmistakable, and keep the next important action easy to find.

LunaPresenter should grow toward the capabilities expected of a serious church presentation system. The inventory below is the **product ambition and planning checklist**, not a claim that all features exist today. Features should be delivered in stages, tested, and marked complete only after they work reliably.

## 4. Intended users

- **Presentation operators** running lyrics, Scripture, announcements, videos, and sermon slides.
- **Worship leaders and musicians** preparing songs, arrangements, lyrics, and service flow.
- **Stage presenters and speakers** who need confidence-monitor information, notes, and current/next content.
- **Production volunteers** who need a clear interface and predictable controls.
- **Media and broadcast teams** coordinating audience screens, stage displays, lobby screens, and stream graphics.
- **Church administrators and service planners** preparing repeatable service plans.
- In the future, other live events that need a similar presentation and screen-control workflow.

## 5. Detailed feature inventory

### A. Service plans, playlists, and rundown

The service rundown is the operator's ordered plan for the event.

- Create, rename, duplicate, reorder, and remove service plans.
- Organize each plan into ordered items such as songs, Scripture, announcements, sermon slides, videos, images, audio, countdowns, and other media.
- Reorder items with drag-and-drop and move items quickly during rehearsal or a live service.
- Add existing library items to a service without recreating them.
- Duplicate items, create reusable templates, and prepare recurring weekly services.
- Support item labels, notes, durations, categories, and optional operator-only instructions.
- Show the selected item, currently live item, slide count, media playback state, and next item clearly.
- Search and filter the rundown and content library.
- Save changes locally, recover saved work, and support explicit import/export and backups.
- Plan for reusable service templates and, later, calendar scheduling and external service-planning integrations.
- Handle unsaved changes visibly and avoid silently losing edits.

### B. Slide editor and presentation content

Provide an editor for creating and maintaining audience-facing slides.

- Create, edit, duplicate, reorder, and delete slides.
- Edit text inline or in a dedicated editor, with a quick-edit workflow for correcting typos during a service.
- Support text formatting, font family and size, weight, alignment, line spacing, colors, and text positioning.
- Control slide backgrounds using solid colors, images, still graphics, and video where supported.
- Add and position text, shapes, images, and media objects.
- Support layers and z-order so text, graphics, and backgrounds can be composed independently.
- Provide slide previews and clear selected-slide states.
- Offer a reflow-style editor to review long text and control where it breaks across slides.
- Allow a long presentation or song to be split into readable slides without losing its content order.
- Provide copy/paste, undo/redo, and sensible edit safeguards as the editor matures.
- Support slide-specific actions, transitions, and timing as later capabilities.
- Make slides readable on large screens and account for safe areas, aspect ratio, and different display dimensions.

### C. Lyrics, songs, and arrangements

Song handling should be a first-class workflow, not just generic text editing.

- Store songs in a searchable song library.
- Organize lyrics into named sections such as verse, chorus, bridge, tag, intro, and outro.
- Build alternate arrangements by reordering or repeating sections without manually duplicating the entire song.
- Generate slides from song sections while allowing manual line breaks and editing.
- Store song title, author/credit fields, notes, and other useful metadata.
- Search songs and quickly add them to the current service.
- Support reusable song formatting through themes.
- Provide a place for chord charts, reference notes, and rehearsal information if added to the roadmap.
- Consider licensed third-party lyric imports and reporting integrations only through their official, authorized interfaces. Do not assume copyrighted lyrics can be freely fetched or redistributed.

### D. Scripture and Bible tools

- Find Scripture by book, chapter, verse, and passage range.
- Display a reference alongside the selected passage.
- Generate readable slides from passages and preserve verse order.
- Support translations and languages where lawful data sources are available.
- Provide configurable verse formatting, reference placement, and slide splitting.
- Search and insert a passage into the current service without losing the operator's place.
- Track the translation used for a passage.
- Treat external Bible text sources and translation licensing as explicit integration requirements, not as assumed free content.

### E. Media library and playback

The media area should provide one place to find and control presentation assets.

- Import and organize images, video clips, audio files, backgrounds, motion backgrounds, and other supported assets.
- Preview media and show file type, dimensions or duration when available.
- Search, sort, categorize, and reuse media across presentations.
- Use images and video as slide backgrounds or foreground objects.
- Provide playback controls for supported audio/video: play, pause, stop, seek, loop, and volume where supported.
- Show playback progress and distinguish a media item that is cued from one that is playing live.
- Support still-image slides, looping background video, and audio playback as browser capabilities permit.
- Provide clear behavior when a file is missing or a format is unsupported.
- Allow users to import local files and export or back up metadata. Avoid silently relying on temporary browser file URLs after a session ends.
- Consider media bins, thumbnail grids, favorites, and recently used assets.
- Plan for playback markers and timed actions as advanced features.
- Treat professional codecs, hardware decoding, multi-channel audio, and broadcast-grade playback as compatibility items requiring real-device testing.

### F. Props and quick overlays

Props are reusable pieces of content that an operator can trigger quickly over the current presentation.

- Create reusable text or media props, such as a logo, lower-third, speaker name, service label, giving prompt, or notification.
- Trigger and dismiss a prop without replacing the current slide.
- Keep props available across the service so an operator can activate them from a dedicated panel or shortcut.
- Define the position, style, size, duration, and intended output for each prop.
- Support transparent backgrounds and layered composition where the output path supports them.
- Allow a prop to appear over slides or media, with explicit rules for which outputs receive it.
- Support multiple props and predictable stacking/clearing behavior.
- Allow props to be triggered by manual action, slide actions, or macros in a later automation system.
- Make it obvious which props are active and provide a reliable clear/dismiss control.

### G. Audience screens and output management

Audience output is what the congregation or event audience sees.

- Keep the operator workspace separate from the audience-facing presentation.
- Provide a dedicated audience output view/window suitable for full-screen display.
- Support previewing the output before sending content live.
- Make live/preview states obvious and prevent accidental confusion between the two.
- Provide controls to go live, advance slides, return to previous slides, clear content, and recover the presentation state.
- Support configurable aspect ratios, scaling, and safe areas.
- Plan for multiple audience outputs with different content, such as main screen, side screens, lobby, overflow room, and stream graphics.
- Provide per-output layouts or “Looks” that control which content layers appear on which display.
- Include operator previews of the content being sent to each output.
- Plan for separate foreground/background layers and key/fill output where the output technology supports it.
- Hardware-specific multi-display routing, SDI, NDI, Syphon, edge blending, and professional key/fill are advanced integration goals, not guaranteed by plain HTML alone.

### H. Stage screens and confidence monitors

Stage screens are private information displays for pastors, speakers, worship leaders, and musicians.

- Provide a separate stage-screen page or window with a layout optimized for confidence monitors.
- Show current slide text and next slide text.
- Display the current service item and what is coming next.
- Display configurable clocks, countdowns, elapsed timers, and time of day.
- Show speaker notes or operator-defined stage notes when appropriate.
- Show chord charts or other rehearsal information if supported by the content.
- Allow operators to send stage-only messages that do not appear on the audience screen.
- Provide high-contrast, large text and configurable layouts for different stage roles.
- Allow stage layout changes during the service and plan for automatic layout changes triggered by service items.
- Provide a preview of the stage output in the operator workspace.
- Support multiple stage layouts and potentially different stage displays for different roles as the output architecture matures.
- Ensure private notes and stage messages are never accidentally shown to the audience.

### I. Countdown timers, clocks, and dynamic text

Timers should be reusable show-control tools, not just text typed onto a slide.

- Countdown to a target time, such as a service start.
- Countdown for a specified duration.
- Elapsed-time timer for a sermon, segment, or event.
- Time-of-day clock.
- Pause, resume, reset, and stop controls where appropriate.
- Display timers on stage screens, audience screens, announcement loops, or selected outputs.
- Provide clear states for running, paused, complete, and not started.
- Support configurable formats, labels, colors, and visibility.
- Support video countdown backgrounds when a suitable video is available.
- Support dynamic text that updates at runtime, such as a timer, clock, current/next item, or configured service information.
- Plan for scheduled starts and service-time reminders.
- Use a dependable timing mechanism and test behavior when a browser tab is backgrounded or a computer sleeps.

### J. Announcements and lobby displays

- Create a separate announcements presentation or loop that can run independently from the main service.
- Build announcement slides with text, images, videos, event details, and reusable layouts.
- Arrange announcements in a loop and set slide duration where supported.
- Prepare lobby, foyer, overflow-room, or pre-service displays.
- Include countdowns, time-of-day clocks, and rotating information.
- Allow announcement content to be prepared ahead of time and reused.
- Plan for scheduled playlists and automatic start/stop behavior.
- Keep the announcements output separate from the main audience output so the two workflows do not interfere.
- Ensure scheduled playback does not imply that the browser can run unattended after the computer sleeps or the browser is closed.

### K. Themes, backgrounds, and visual design

- Create reusable themes for typography, colors, alignment, text placement, and background treatment.
- Apply a theme to one slide, a presentation, or a group of slides.
- Update a theme and propagate the change to linked slides when appropriate.
- Maintain consistent styles for lyrics, Scripture, announcements, sermon notes, and lower-thirds.
- Support still and motion backgrounds, image fills, color fills, and media fills where supported.
- Provide text and background effects with performance-conscious defaults.
- Support transitions between slides and media where the browser can render them reliably.
- Support shapes, masks, transparency, and compositing as the editor matures.
- Include practical presets for common church screens and widescreen layouts.
- Keep the editor intuitive instead of overwhelming volunteers with unnecessary visual controls.

### L. Live controls, clearing, and operator views

- Provide previous/next slide and previous/next item controls.
- Support keyboard shortcuts with an on-screen shortcut reference.
- Provide dedicated controls to clear the slide, background, media, props, or selected output.
- Include an operator overview showing preview, live output, active media, selected item, and next item.
- Make the currently live content unmistakable.
- Support live edits when safe, without unexpectedly blanking or interrupting output.
- Provide quick search across presentations and libraries.
- Allow the operator to jump to a particular slide or section.
- Provide visible feedback when an action succeeds or fails.
- Include a safe recovery path if the selected item or media cannot be displayed.
- Keep high-risk actions such as clearing all outputs or ending a show clear and deliberate.

### M. Automation, actions, macros, and timelines

- Attach actions to slides or service items, such as starting or stopping media, showing a prop, clearing a layer, or changing a stage layout.
- Create macros: named sequences of actions that can be triggered manually or by another supported event.
- Provide a simple automation editor with readable action ordering and error feedback.
- Support playback markers that trigger an action at a chosen point in a media timeline.
- Build timelines that can coordinate slide changes, media, and actions at configured times.
- Plan for timecode-based synchronization where a reliable timecode source and supported integration are available.
- Support calendar-based scheduling for announcements and pre-service content as a later feature.
- Ensure automations can be inspected, stopped, and safely overridden by the operator.
- Never let an automation silently take over the live output without clear configuration and feedback.

### N. External control and production integrations

These are long-term capabilities whose feasibility depends on browser APIs, documented protocols, hardware, and possibly companion services.

- A documented local API or integration layer for approved control commands.
- Remote control from another device on the same network, with appropriate access control.
- MIDI triggers and cues where a supported browser or bridge can provide access.
- DMX/lighting integration through a supported protocol or companion service.
- Stream Deck or similar programmable control surfaces through an official integration or bridge.
- Planning Center Services or other service-planning integrations where APIs and permissions allow.
- Authorized lyric and Bible content integrations.
- NDI, SDI, Syphon, alpha/key-fill, and external video input/output as advanced broadcast goals requiring compatible software or hardware.
- Network linking between operator instances, alternate outputs, and redundancy.
- Timecode synchronization with compatible systems.
- Clear status and error messages for disconnected devices or unavailable integrations.

Do not claim that a listed integration works until it has been implemented and tested with the required software, hardware, permissions, and environment.

### O. Import, export, storage, and reliability

- Save service plans and application preferences locally during the early browser-only stage.
- Export and import service data in a documented format such as JSON.
- Support backups and recovery of service content.
- Handle malformed imports and missing assets without corrupting existing work.
- Clearly explain which media files are embedded, linked, or must be selected again after reopening.
- Avoid silent data loss and show when changes are unsaved.
- Use versioned data structures so future releases can migrate older service files.
- Plan for cloud backup, cross-device sync, accounts, and team sharing only when the project is ready for a backend or suitable service.
- Make privacy and data ownership explicit.
- Test the app after refresh, restart, file import, and typical service workflows.

### P. Accessibility, usability, and responsive behavior

- Use clear visual hierarchy, readable type, and high-contrast status indicators.
- Provide keyboard access and visible focus indicators for controls.
- Make the interface usable at common laptop and desktop sizes.
- Adapt gracefully to smaller screens for preparation and basic remote control, while recognizing that live multi-output production generally needs a desktop-class setup.
- Avoid relying on color alone to communicate live/preview or error states.
- Provide helpful empty states, loading states, confirmation, and error feedback.
- Optimize routine actions for quick access and reduce unnecessary modal dialogs.
- Keep the interface responsive while media and timers are active.

## 6. Suggested product modules

The application can be organized into coherent modules as it grows:

1. **Presenter** — main operator view, preview, live controls, slide navigation, and output status.
2. **Service Plans** — rundowns, playlists, reusable service templates, and item ordering.
3. **Slide Editor** — slide content, layouts, themes, layers, and reflow editing.
4. **Media Library** — images, video, audio, backgrounds, and imported assets.
5. **Songs** — lyrics, song sections, arrangements, and song metadata.
6. **Scripture** — passage lookup, translation selection, and Scripture slide creation.
7. **Props** — reusable overlays, quick graphics, and on-demand text/media.
8. **Stage Screens** — confidence-monitor layouts, current/next content, stage messages, notes, and clocks.
9. **Timers** — countdowns, elapsed timers, time-of-day clocks, and dynamic text.
10. **Announcements** — independent lobby/pre-service loops and scheduled content.
11. **Outputs & Looks** — audience outputs, stage outputs, per-screen layouts, and output previews.
12. **Automation** — actions, macros, timelines, playback markers, and supported external triggers.
13. **Settings & Integrations** — preferences, shortcuts, import/export, and future connection setup.

These are organizational targets; they do not require every module to exist in the first version.

## 7. Product principles

- **HTML-first:** build the application experience with HTML, CSS, and JavaScript.
- **Operator-first:** optimize for the person running the service.
- **Reliable under pressure:** prioritize predictable state, clear controls, and recovery.
- **Simple to learn:** support volunteers without sacrificing capability for experienced operators.
- **Fast workflows:** reduce friction between service items and slides.
- **Audience readability:** optimize typography and content for large screens.
- **Separation of concerns:** keep audience content, stage-only information, preview, and live output distinct.
- **Honest capability claims:** distinguish implemented, tested features from planned integrations.
- **Progressive development:** ship useful vertical slices rather than a collection of nonfunctional buttons.
- **Data ownership:** make saving, backup, export, and import dependable priorities.
- **Maintainability:** avoid unnecessary complexity while keeping code understandable for future contributors.

## 8. Development strategy

Build and test the product in stages.

### Stage 1 — Core HTML presenter

- Establish the HTML/CSS/JavaScript application shell and visual design system.
- Build service rundown management.
- Build slide creation and editing.
- Implement preview and a separate audience output.
- Add basic keyboard navigation, local saving, and JSON import/export.
- Test the core service flow end to end.

### Stage 2 — Content and media

- Improve the media library and supported playback.
- Add reusable themes and backgrounds.
- Build dedicated song and Scripture workflows.
- Add quick editing, search, and reusable service templates.

### Stage 3 — Stage and live-service tools

- Build stage-screen output and configurable layouts.
- Add current/next content and stage-only messages.
- Add countdowns, clocks, elapsed timers, and dynamic text.
- Build props and quick overlays.
- Add announcement and lobby loops.

### Stage 4 — Advanced production workflows

- Add output/Look management, layered composition, and richer slide actions.
- Develop macros, timelines, playback markers, and automation.
- Investigate remote control and integrations based on documented APIs and real technical constraints.
- Evaluate multi-output, broadcast, and hardware workflows individually.

### Stage 5 — Sync, collaboration, and operational maturity

- Evaluate cloud sync, team sharing, user accounts, and external service planning.
- Improve backup, recovery, migration, and diagnostics.
- Add automated regression checks and repeatable release procedures.

This sequence is a starting roadmap, not a promise that every stage has a fixed deadline.

## 9. Definition of done

A feature is not complete simply because its button or screen exists. A feature should be considered complete only when:

- Its expected behavior is documented.
- Its primary workflow is implemented and testable.
- It has been checked in the target browser(s).
- It does not break existing presenter workflows.
- Error and empty states are handled.
- Any required permissions, hardware, external accounts, or integrations are documented.
- The documentation accurately states its limitations.
- The project roadmap is updated to reflect its real status.

## 10. Team roles and collaboration

- **Product owner:** sets the vision, priorities, and acceptance decisions.
- **Claude — lead coder:** writes and modifies code, implements features, debugs, and runs code-level tests.
- **ChatGPT — operations support:** coordinates tasks, maintains the roadmap and documentation, clarifies requirements, tracks blockers, helps organize QA, and supports release planning.

The GitHub repository is the shared source of truth for project files, plans, and decisions. Work should be divided into clear, reviewable tasks with acceptance criteria. ChatGPT and Claude do not automatically share conversation context, so important decisions should be written into repository documentation or issues.

## 11. Current status

LunaPresenter is an evolving project. This document describes the product vision and desired capabilities; it is **not a statement that every listed feature has already been built**. Maintain a separate implementation status or roadmap that marks each capability as planned, in progress, implemented, or tested.

The long-term objective is to build a dependable, modern, HTML-based presentation and live-production workspace that helps church teams prepare and deliver services smoothly and confidently.

## 12. Reference for feature planning

The breadth of this specification is informed in part by the publicly described ProPresenter feature categories, including media and slides, stage displays, timers, props, announcements, automation, multi-screen management, and production integrations:

- ProPresenter feature overview: https://renewedvision.com/propresenter/all-features
- ProPresenter stage display overview: https://renewedvision.com/propresenter/stage-display
- ProPresenter user guide: https://learn.renewedvision.com/propresenter

LunaPresenter is an independent project with its own implementation and product identity. This list is a planning reference, not a claim of feature equivalence, affiliation, or compatibility.
