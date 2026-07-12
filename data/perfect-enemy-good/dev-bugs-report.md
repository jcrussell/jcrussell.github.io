# Forge fork — bugs fixed vs upstream

_Scope: every bug worked on across the fork's life (`upstream/main..dev`), both the pre-beads era (git history) and the beads era (bd tracker), deduplicated on GitHub issue number. Verified read-only against `upstream/main` (forge-ext/forge)._

## Summary

- **203 product bugs fixed** (80 from GitHub issues, 123 internally discovered).
- **Origin of fixed bugs:** 160 inherited from upstream, **42 self-inflicted regressions** we introduced and then fixed.
- **Upstream status:** 157 of our inherited fixes are still **unfixed in upstream/main** (not upstreamed); 5 were also fixed independently upstream.
- **Still unfixed:** 34 product bugs remain open/in-progress/deferred.
- 4 closed as not-a-defect / duplicate.
- Plus 39 test/CI/E2E-infrastructure issues (appendix).
- Totals: 280 rows · eras: beads=169, both=32, pre-beads=79.

> **Note — independently fixed upstream:** forge-bomy (Partial); forge-w35r (Partial); forge-5r0j (Partial); forge-n29i (Partial); 1517ee7 (Partial).

## 1. GitHub-reported bugs we fixed

| Ref | Bug | Area | Origin | In upstream/main? | Fixed in | Status |
|---|---|---|---|---|---|---|
| #294 | Tile/window override configuration handling | config | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #415 | Corrupt config file is not handled gracefully on load | config | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #350 | Add portable config sync for settings and keybindings | config | Inherited | Yes (still present) | pre-beads `97a5a60` | Fixed |
| #453 | Wayland window ID toggle: wmId not checked for per-window overrides | config | Inherited | Yes (still present) | pre-beads `d8ea2d9` | Fixed |
| #529 / forge-63y | Stray red preview window appears when moving a tab | decoration | Inherited | Yes (still present) | beads `d51639d` | Fixed |
| #303 / forge-iwi | Tab decorator disappears randomly via the minimized/maximized/fullscreen suppression path | decoration | Inherited | Yes (still present) | both (pre `1da5d63`, bd `5a4222c`) | Fixed |
| #164 / forge-uqx | Tiled outline/hint drawn at wrong size on Wayland HiDPI | decoration | Inherited | Yes (still present) | both (pre `9d361fd`, bd `6334519`) | Fixed |
| #297 | Hide floating window border when tiling is disabled (gh#297) | decoration | Inherited | Yes (still present) | pre-beads `fb84f7d` | Fixed |
| #262 | Hide focus border when only a single window is present | decoration | Inherited | Yes (still present) | pre-beads `db2f449` | Fixed |
| #268 | Focus hint stuck on screen after workspace change | decoration | Inherited | Yes (still present) | pre-beads `93456a1` | Fixed |
| #472 / forge-0z2 | Evolution email client window always floats instead of tiling | float | Inherited | Yes (still present) | both (pre `93456a1`, bd `8e65a19`) | Fixed |
| #469 / forge-w7e | Always-on-top windows break layering/behaviour under Forge tiling | float | Inherited | Yes (still present) | both (pre `93456a1`, bd `dc76b5f`) | Fixed |
| #292 | Toggle float for a window addressed by wmId | float | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #387 | Float exemption logic mis-classifies windows that should/shouldn't float | float | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #172 | Per-window float toggle now affects only the targeted window, not all windows (gh#172) | float | Inherited | Yes (still present) | pre-beads `8068052` | Fixed |
| #319 | Float always-on-top state properly tracked and cleared when float toggled off (gh#319) | float | Inherited | Yes (still present) | pre-beads `8068052` | Fixed |
| #426 | Chrome window stuck always-on-top | float | Inherited | Yes (still present) | pre-beads `93456a1` | Fixed |
| #171 | Remember last-focused window within containers | focus | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #230 | Focus navigation between stacked groups | focus | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #258 | Transfer focus to a sensible sibling when a window closes | focus | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #40 | Focus navigation now skips minimized windows in containers | focus | Inherited | Yes (still present) | pre-beads `6576599` | Fixed |
| #227 | Use last focused window as fallback target when tiling newly opened windows (gh#227) | focus | Inherited | Yes (still present) | pre-beads `7bedfda` | Fixed |
| #396 | Don't focus notifications/popups on hover-to-focus (gh#396) | focus | Inherited | Yes (still present) | pre-beads `f3a4578` | Fixed |
| #458 | Option to restrict hover-to-focus to only while tiling is active (default off) (gh#458) | focus | Inherited | Yes (still present) | pre-beads `f3a4578` | Fixed |
| #483 | Hover-to-focus steals focus and breaks password dialogs | focus | Inherited | Yes (still present) | pre-beads `93456a1` | Fixed |
| #249 / forge-m37 | Keyboard shortcuts collide with GNOME native Super+L lock shortcut | keybinding | Inherited | Yes (still present) | both (pre `7790e12`, bd `7030285`) | Fixed |
| #165 | Add 'Disable All' and 'Restore Defaults' buttons for keyboard shortcuts | keybinding | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #414 | Add window-pointer-to-focus keybinding (default unbound) | keybinding | Inherited | Yes (still present) | pre-beads `629a163` | Fixed |
| #287 | Add workspace-monocle-toggle keybinding (default unbound) | keybinding | Inherited | Yes (still present) | pre-beads `629a163` | Fixed |
| #308 | Add Shift+Super+R keybinding to reload config from files | keybinding | Inherited | Yes (still present) | pre-beads `322b472` | Fixed |
| #530 / forge-nh7 | Conflict with Burn My Windows extension breaks tiling/placement | lifecycle | Inherited | Yes (still present) | beads `572402a` | Fixed |
| #401 / forge-bqa | Stacked/tabbed groups are lost after waking from sleep | lifecycle | Inherited | Yes (still present) | beads `82ca53c` | Fixed |
| #379 / forge-2zj | Multi-display navigation keybindings do not work | multimonitor | Inherited | Yes (still present) | beads `a038ef5` | Fixed |
| #78 | Handle display disconnect/reconnect cleanly | multimonitor | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #295 | Add monitor-skip-tile setting to exclude specific monitors from tiling (gh#295) | multimonitor | Inherited | Yes (still present) | pre-beads `7bedfda` | Fixed |
| #316 / forge-4a6 | Shortcut editing in preferences is slow until EntryRow saves are debounced | prefs | Inherited | Yes (still present) | both (pre `334eb47`, bd `?`) | Fixed |
| #321 | Cheatsheet organization improved with tables and section spacing | prefs | Inherited | Yes (still present) | pre-beads `0a0de2e` | Fixed |
| #133 | Move search entry to top of Floating Windows prefs section | prefs | Inherited | Yes (still present) | pre-beads `130800c` | Fixed |
| #439 | Disable experimental options (stacked/tabbed tiling) by default | prefs | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #272 | Add screen edge margin settings (top/bottom/left/right) | prefs | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #158 | Add tab margin customization in preferences | prefs | Inherited | Yes (still present) | pre-beads `fb84f7d` | Fixed |
| #365 | Add tab margin customization in preferences | prefs | Inherited | Yes (still present) | pre-beads `fb84f7d` | Fixed |
| #435 | Increase gap multiplier cap from 8 to 32 | prefs | Inherited | Yes (still present) | pre-beads `629a163` | Fixed |
| #398 | Add default-window-layout setting (tiled/tabbed/stacked) | prefs | Inherited | Yes (still present) | pre-beads `629a163` | Fixed |
| #286 | Separate panel tray icon from the quick settings toggle | prefs | Inherited | Yes (still present) | pre-beads `db2f449` | Fixed |
| #532 / forge-5v6 | Holding the window-resize shortcut does not repeat/work for tiled windows | resize | Inherited | Yes (still present) | beads `8bd8656` | Fixed |
| #497 / forge-pak | Resizing a tabbed window does not actually resize it | resize | Inherited | Yes (still present) | both (pre `9d361fd`, bd `06d073a`) | Fixed |
| #305 / forge-12f | Resizing one tile boundary also shifts the opposite boundary due to cumulative debit drift | resize | Inherited | Yes (still present) | both (pre `1a9aff3`, bd `192036c`) | Fixed |
| #64 | Resize the front tab within a tabbed container | resize | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #348 | Expand/shrink keybinds (Super+]/[) work in all directions | resize | Inherited | Yes (still present) | pre-beads `fb84f7d` | Fixed |
| #312 / forge-9sd | Color/theme changes not saved because user stylesheet was read-only on write | theme | Inherited | Yes (still present) | both (pre `f91b2d9`, bd `3ee82bd`) | Fixed |
| #448 | CSS declaration parsing fails on malformed stylesheet declarations | theme | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #45 | Panel overlap with tiled windows fixed via configurable workspace margin settings (gh#45) | theme | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #361 | Add border radius setting (0-30px) in Appearance preferences | theme | Inherited | Yes (still present) | pre-beads `322b472` | Fixed |
| #266 | Theme backup written as undefined.bak due to missing name | theme | Inherited | Yes (still present) | pre-beads `93456a1` | Fixed |
| #175 / forge-2gn | Drag preview overlay stays stuck on screen when arranging windows with the mouse | tiling | Inherited | Yes (still present) | both (pre `1da5d63`, bd `bb880c7`) | Fixed |
| #509 / forge-fw8 | Fullscreen window misbehaves when a second app is running | tiling | Inherited | Yes (still present) | beads `fa74c2f` | Fixed |
| #482 / forge-3qq | Anki window does not get tiled | tiling | Inherited | Yes (still present) | both (pre `a488b6b`, bd `85e925a`) | Fixed |
| #470 / forge-6qr | Closing windows disrupts tiling on other workspaces | tiling | Inherited | Yes (still present) | both (pre `9d361fd`, bd `1966856`) | Fixed |
| #461 / forge-9yo | Window can be edge-snapped/maximized while in tiling mode | tiling | Inherited | Yes (still present) | both (pre `93456a1`, bd `aedc184`) | Fixed |
| #436 / forge-7m3 | New window re-equalizes sibling sizes instead of preserving percents | tiling | Inherited | Yes (still present) | beads `8c45267` | Fixed |
| #322 / forge-mme | ddterm window blinks because Forge tries to tile/resize it; fixed by wm_class filter | tiling | Inherited | Yes (still present) | both (pre `5582414`, bd `?`) | Fixed |
| #311 / forge-5ng | Incorrect tiling layout on tall (portrait) monitors | tiling | Inherited | Yes (still present) | both (pre `8068052`, bd `e7233d8`) | Fixed |
| #309 / forge-eca | Huge black/white empty XWayland Video Bridge window tiled; fixed by wm_class filter | tiling | Inherited | Yes (still present) | both (pre `1da5d63`, bd `?`) | Fixed |
| #271 / forge-khb | Steam app tiles but window size overlaps neighbors | tiling | Inherited | Yes (still present) | both (pre `a488b6b`, bd `7e8f34a`) | Fixed |
| #117 / forge-ypn | Apps render partially off-screen when tiled near monitor edges | tiling | Inherited | Yes (still present) | both (pre `a488b6b`, bd `8a92915`) | Fixed |
| #57 / forge-37r | Stacking/tabbing windows that have split-con siblings produced broken layout | tiling | Inherited | Yes (still present) | both (pre `1a9aff3`, bd `00993a6`) | Fixed |
| #330 | 2x2 tiling layout computes incorrect window heights | tiling | Inherited | Yes (still present) | pre-beads `a488b6b` | Fixed |
| #408 | Upstream feature request gh#408 already implemented in fork; closed as already-implemented | tiling | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #281 | Upstream feature request gh#281 already implemented in fork; closed as already-implemented | tiling | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #419 | Upstream feature request gh#419 already implemented in fork; closed as already-implemented | tiling | Inherited | Yes (still present) | pre-beads `334eb47` | Fixed |
| #462 | Auto-unmaximize maximized windows when a new window is tiled (default on) (gh#462) | tiling | Inherited | Yes (still present) | pre-beads `f3a4578` | Fixed |
| #315 | Add option to auto-maximize a lone window (default off) | tiling | Inherited | Yes (still present) | pre-beads `fb84f7d` | Fixed |
| #382 | Add evenly-distribute-windows keybind (Super+=) | tiling | Inherited | Yes (still present) | pre-beads `db2f449` | Fixed |
| #433 | Track dragged window in _handleGrabOpBegin during drag-tiling | tiling | Inherited | Yes (still present) | pre-beads `1cfc0d1` | Fixed |
| #407 | Split direction hint never appears because maximized check was a function ref, not called | tiling | Inherited | Yes (still present) | pre-beads `9d361fd` | Fixed |
| #409 | Split direction hint not appearing (maximized check uncalled) - duplicate report of #407 | tiling | Inherited | Yes (still present) | pre-beads `9d361fd` | Fixed |
| #411 | Waydroid gaps: skip app-specific gaps for non-standard window frames | tiling | Inherited | Yes (still present) | pre-beads `d8ea2d9` | Fixed |
| #416 | Wayland stacking: ensure tiled windows appear above the desktop layer | tiling | Inherited | Yes (still present) | pre-beads `d8ea2d9` | Fixed |
| #374 | Workspace focus jump: skip focus during workspace transitions | workspace | Inherited | Yes (still present) | pre-beads `d8ea2d9` | Fixed |

## 2. Internally-discovered bugs we fixed

| Ref | Bug | Area | Origin | In upstream/main? | Fixed in | Status |
|---|---|---|---|---|---|---|
| forge-0rb6 | Cheatsheet overlay has no reliable dismiss path (Escape/click-outside/close-X all missing) | cheatsheet | Self-inflicted | n/a (self-inflicted) | beads `aa6d3a4` | Fixed |
| forge-k5m6 | Cheatsheet overlay centered once at show() and never re-positioned on monitor/resolution change | cheatsheet | Self-inflicted | n/a (self-inflicted) | beads `aa6d3a4` | Fixed |
| forge-v3y3 | Cheatsheet.show() re-adds an already-parented overlay (Clutter double-parent) during the hide ease | cheatsheet | Self-inflicted | n/a (self-inflicted) | beads `9f3cef1` | Fixed |
| forge-3t3a | importAll() re-entrantly schedules exportAll(), rewriting the file just imported (no in-flight guard) | config | Self-inflicted | n/a (self-inflicted) | beads `4406864` | Fixed |
| forge-orrf | init() force-re-enables config-file-sync on every startup, overriding a user who disabled auto-sync | config | Self-inflicted | n/a (self-inflicted) | beads `4406864` | Fixed |
| forge-el01 | 'Auto-sync changes' toggle ignored at runtime; auto-export cannot be turned off without restart | config | Self-inflicted | n/a (self-inflicted) | beads `5b888c9` | Fixed |
| forge-8rm6 | reloadWindowOverrides strips live per-window float overrides, re-tiling them after any prefs edit | config | Inherited | Yes (still present) | beads `4406864` | Fixed |
| forge-3sv2 | windowProps setter wrote to read-only bundled config on fresh install, silently losing the first override | config | Inherited | Yes (still present) | beads `e40a851` | Fixed |
| forge-96e | Empty/corrupt windows.json made windowProps null, crashing all tiling on .overrides dereference | config | Inherited | Yes (still present) | beads `b19d268` | Fixed |
| forge-x55z | Docs/schema claim wmClass rules use substring matching but code is exact per-comma-token equality, so partial-class rules silently never match | config | Self-inflicted | n/a (self-inflicted) | beads `8e65a19` | Fixed |
| forge-eny3 | gschema keys focus-border-size/-color, split-border-color, primary-layout-mode are read by nothing yet exported/documented as live knobs | config | Inherited | Yes (still present) | beads `30efe82` | Fixed |
| forge-nuny | config-sync whitelists are stale, silently dropping 4 settings + 5 keybindings on export/import and rejecting them as schema-invalid | config | Self-inflicted | n/a (self-inflicted) | beads `30efe82` | Fixed |
| forge-6c0e | Startup stale-wmId override prune is cache-only, resurrected by first window close; unbounded windows.json cruft | config | Inherited | Yes (still present) | beads `e67ebef` | Fixed |
| forge-rt10 | config-sync auto-export resurrects a user-deleted portable file when only one of the two was deleted | config | Self-inflicted | n/a (self-inflicted) | beads `a5e283f` | Fixed |
| forge-nn0m | Prefs Import/Export and the extension's debounced exportAll clobber the same JSON with no coordination | config | Self-inflicted | n/a (self-inflicted) | beads `a5e283f` | Fixed |
| forge-qj5n | Auto-export silently resurrects portable config files the user deliberately deleted | config | Self-inflicted | n/a (self-inflicted) | beads `a5e283f` | Fixed |
| forge-f6go | ConfigManager decodes windows.json via legacy imports.byteArray.toString instead of TextDecoder | config | Inherited | Yes (still present) | beads `6a7a2d5` | Fixed |
| forge-u7xz | ConfigManager.loadFile first-run path leaves empty file / does no-op windows.json rewrites | config | Inherited | Yes (still present) | beads `9634940` | Fixed |
| forge-v2yz | use-after-dispose: _destroyDecoration leaves child .tab dangling, crashing on close in stacked/tabbed | decoration | Self-inflicted | n/a (self-inflicted) | beads `2b01d6a` | Fixed |
| forge-bomy | Tabbed tab actor double-parented on keyboard swap, tripping a Clutter assertion that crashes shell | decoration | Inherited | Partial | beads `2b01d6a` | Fixed |
| forge-qy65 | Tab-bar icons double-scaled at integer HiDPI, distorting icons in every stacked/tabbed tab bar | decoration | Inherited | Yes (still present) | beads `a774188` | Fixed |
| forge-wrot | Closed tabbed/stacked window's tab St.BoxLayout never destroyed (actor + signal leak per close) | decoration | Inherited | Yes (still present) | beads `af054bb` | Fixed |
| forge-m2oe | Yellow split-direction hint border overshoots the window's rounded corners | decoration | Inherited | Yes (still present) | beads `12845c8` | Fixed |
| forge-2uc0 | Window with null WindowTracker app at map time never gets a tab bar entry | decoration | Inherited | Yes (still present) | beads `d8583b4` | Fixed |
| forge-gdsz | Reparenting/flattening a tabbed CON destroys surviving windows' tab actors, so the next render throws | decoration | Inherited | Yes (still present) | beads `a3f993f` | Fixed |
| forge-hcbz | Focus/split border inset is raw 3px while CSS border-width is dpi-scaled, so the border paints over window content at integer HiDPI | decoration | Inherited | Yes (still present) | beads `a774188` | Fixed |
| forge-6asv | Reparenting a stacked/tabbed CON destroys child tab actors without nulling dangling node.tab refs | decoration | Inherited | Yes (still present) | beads `2b01d6a` | Fixed |
| forge-ogmd | Decoration self-heal catch nulls node.decoration without destroying the orphaned St.BoxLayout | decoration | Self-inflicted | n/a (self-inflicted) | beads `23e5474` | Fixed |
| forge-36le | Yellow split-direction hint border never paints on Wayland because border-radius is also set | decoration | Inherited | Yes (still present) | beads `6b0e5a7` | Fixed |
| forge-5r0j | Vacuous _destroyed guard on tab actors risks finalized-actor throw in nested tabbed churn | decoration | Self-inflicted | Partial | beads `23e5474` | Fixed |
| forge-s7qo | processTabbed error recovery nulls node.decoration but never recreates it, leaving an unhideable orphan | decoration | Self-inflicted | n/a (self-inflicted) | beads `2a20d34` | Fixed |
| forge-v4u0 | _createWindowTab passes a null app to create_icon_texture, throwing on an app-less tabbed window | decoration | Inherited | Yes (still present) | beads `f1d7198` | Fixed |
| 4066921 | Split-direction hint only shown with a single child, never with 2+ windows in a container | decoration | Inherited | Yes (still present) | pre-beads `4066921` | Fixed |
| 2ae085c | Border hidden when window is alone in its container but sibling containers hold other windows | decoration | Inherited | Yes (still present) | pre-beads `2ae085c` | Fixed |
| forge-te9o | processFloats clobbers GRAB_TILE->TILE on a mid-drag force render, silently no-opping drag tiling | float | Inherited | Yes (still present) | beads `1207861` | Fixed |
| forge-5l9b | Queued raise-float event restacks a demoted float over a fullscreen window, permanently undoing float demotion | float | Self-inflicted | n/a (self-inflicted) | beads `28dbe36` | Fixed |
| forge-08he | Dialogs permanently pinned always-on-top, so a sibling float can never be raised above them | float | Self-inflicted | n/a (self-inflicted) | beads `0159a15` | Fixed |
| forge-h7ba | Float cleanup/override paths call Meta.Window accessors without liveness guard; finalized wrapper throws | float | Inherited | Yes (still present) | beads `bf04456` | Fixed |
| forge-fov0 | Removing one float override deletes every override sharing the same wmClass | float | Inherited | Yes (still present) | beads `92a8a6a` | Fixed |
| forge-fxf | Super+c could not re-tile a window floated via Super+Shift+c because per-window toggle ignored class float | float | Inherited | Yes (still present) | beads `b6f5e51` | Fixed |
| forge-t1s9 | Float*Toggle dereferences existParent without null guard (inconsistent with WindowResetSizes) | float | Inherited | Yes (still present) | beads `c57ebd5` | Fixed |
| forge-jbkg | Class-only tile override short-circuits floatByType heuristics, force-tiling that class's dialogs | float | Self-inflicted | n/a (self-inflicted) | beads `b8177a1` | Fixed |
| forge-n29i | Title-only float override (no wmClass) never matches; also crashed the prefs Windows page on open | float | Inherited | Partial | beads `aab213f` | Fixed |
| forge-2ew | Transient dialog lands behind its right tiled neighbor; Forge never repositions occluded floats | float | Inherited | Yes (still present) | beads `4c48177` | Fixed |
| 428bed8 | Dialog/transient windows could appear behind tiled windows instead of being raised | float | Inherited | Yes (still present) | pre-beads `428bed8` | Fixed |
| 22ccd46 | resolveX/Y crashed using `this` to call module functions when centering/aligning windows | float | Inherited | Yes (still present) | pre-beads `22ccd46` | Fixed |
| forge-ph7f | Rapid focus navigation strands windows always-on-top and un-tiles them into overlap on Wayland | focus | Self-inflicted | n/a (self-inflicted) | beads `c0cffa9` | Fixed |
| forge-jnfk | Missing GLib import in tree.js makes Wayland directional focus throw, leaving windows permanently floating | focus | Self-inflicted | n/a (self-inflicted) | beads `9489e37` | Fixed |
| forge-d5mm | Plain focus calls updateStacked/TabbedFocus() with no arg, so they no-op (no re-stack/raise) | focus | Inherited | Yes (still present) | beads `a9b6e0f` | Fixed |
| forge-lqe5 | Stacked-focus returned a nested CON (or minimized) lastChild, crashing metaWindow.raise() on an St.Bin | focus | Inherited | Yes (still present) | beads `c7ced6a` | Fixed |
| forge-f081 | postProcessWindow passes a Meta.Window to movePointerWith (Node expected), so new-window pointer-warp has never worked | focus | Inherited | Yes (still present) | beads `0d38d8c` | Fixed |
| forge-62ja | _handleGrabOpEnd focus-lost early return leaves this.grabOp stale, defeating the WINDOW_BASE guard | focus | Inherited | Yes (still present) | beads `a9b6e0f` | Fixed |
| forge-leqs | Operator-precedence bug: !grabOp === WINDOW_BASE always false, so updateTabbedFocus never called on re-home | focus | Inherited | Yes (still present) | beads `cc27b2d` | Fixed |
| forge-s02h | storePointerLastPosition calls get_frame_rect() on a possibly-disposed lastFocusedWindow (no liveness guard) | focus | Inherited | Yes (still present) | beads `8bd8656` | Fixed |
| forge-ipga | FloatToggle and resize() keybindings threw when invoked with no (or untracked) focused window | keybinding | Inherited | Yes (still present) | beads `c57ebd5` | Fixed |
| forge-u7t0 | Cheatsheet calls get_strv() on string-typed mod-mask-mouse-tile, logging one GLib CRITICAL per open | keybinding | Self-inflicted | n/a (self-inflicted) | beads `8e65a19` | Fixed |
| 8f67e10 | Forge Super+H (focus-left) conflicts with GNOME's default minimize keybinding | keybinding | Inherited | Yes (still present) | pre-beads `8f67e10` | Fixed |
| forge-lvhp | Tracked dialog signals leak on disable() because the cleanup loop iterates a tab list that excludes dialogs | lifecycle | Inherited | Yes (still present) | beads `2dac071` | Fixed |
| forge-rj4x | media-keys GSettings override can hard-abort gnome-shell when a schema/key is absent | lifecycle | Self-inflicted | n/a (self-inflicted) | beads `8e6298a` | Fixed |
| forge-5y6j | Untracked settings 'changed' handler keeps firing on a zombie WindowManager after disable() | lifecycle | Inherited | Yes (still present) | beads `9489e37` | Fixed |
| forge-h6jc | Tree scaffold bins never removed from window_group on disable or reload, accumulating actors | lifecycle | Inherited | Yes (still present) | beads `b852687` | Fixed |
| forge-606o | _workspaceChangingTimeoutId never cleared in _removeSignals: 300ms timer outlives disable() | lifecycle | Self-inflicted | n/a (self-inflicted) | beads `b852687` | Fixed |
| forge-16ms | Windows never tile on non-primary monitors under GNOME default workspaces-only-on-primary=true | multimonitor | Self-inflicted | n/a (self-inflicted) | beads `7fd35de` | Fixed |
| forge-tpgh | Shell crash: get_work_area_current_monitor aborts (libmutter g_assert) on a window with no logical monitor | multimonitor | Inherited | Yes (still present) | beads `2e62999` | Fixed |
| forge-s7ri | Keyboard Move at a display edge teleports the window to the pointer's monitor, not its own | multimonitor | Inherited | Yes (still present) | beads `6fbf9be` | Fixed |
| forge-e3k1 | move() cross-monitor branch commits the reparent before extWm.move/get_work_area can throw | multimonitor | Inherited | Yes (still present) | beads `a33bf77` | Fixed |
| forge-wqlx | Single shared _wsWindowAddSrcId debounce coalesces window-added across workspaces, dropping events | multimonitor | Inherited | Yes (still present) | beads `35da017` | Fixed |
| forge-e3xm | move() min-size clamp uses source monitor work area, bouncing cross-monitor moves of min-size windows | multimonitor | Inherited | Yes (still present) | beads `efa0456` | Fixed |
| forge-cm69 | rectForMonitor cross-monitor transform uses absolute coords in '>' branches, computing off-target rects | multimonitor | Inherited | Yes (still present) | beads `b8177a1` | Fixed |
| forge-w3ss | SpinButtonRow bind and onChange are mutually exclusive, so Border radius/Tab margin CSS never updates | prefs | Self-inflicted | n/a (self-inflicted) | beads `7e555d1` | Fixed |
| forge-3qj3 | EntryRow debounce timeout never cancelled on teardown; save() fires on a finalized prefs widget | prefs | Self-inflicted | n/a (self-inflicted) | beads `a1f5969` | Fixed |
| forge-egnf | DropDownRow.reset() forces index 0, clobbering the GSettings default ResetButton just restored | prefs | Inherited | Yes (still present) | beads `a1f5969` | Fixed |
| forge-l64o | monitor-skip-tile missing from the settings-changed switch, so 'Non-tiling monitors' prefs edits do nothing until an unrelated render | prefs | Self-inflicted | n/a (self-inflicted) | beads `d720e5d` | Fixed |
| forge-4w7e | Classless title-only float rule shows a blank subtitle in the prefs Windows page | prefs | Inherited | Yes (still present) | beads `6f9ac3d` | Fixed |
| forge-34c6 | _handleResizing indexes childNodes out of bounds at a container boundary, throwing during live resize | resize | Inherited | Yes (still present) | beads `7ae8cf3` | Fixed |
| forge-hs6l | nextVisible passes -1 sentinel through; _handleResizing assigns .percent on it, throwing TypeError | resize | Inherited | Yes (still present) | beads `9ba22bc` | Fixed |
| forge-gm0z | WindowExpand/Shrink fired four overlapping resize grabs that clobbered grabOp, so window never grew vertically | resize | Self-inflicted | n/a (self-inflicted) | beads `9ba22bc` | Fixed |
| forge-74em | Keyboard resize Top/Bottom anchored the wrong vertical edge, moving the opposite side from requested | resize | Inherited | Yes (still present) | beads `10eb666` | Fixed |
| forge-ue92 | _grabCleanup re-walks post-reparent ancestors, stranding stale initRect on tabbed container after drag-out; next tab resize jumps | resize | Self-inflicted | n/a (self-inflicted) | beads `69e6863` | Fixed |
| forge-v4wh | Maximize/fullscreen during the 120ms keyboard-resize debounce is consumed as a resize delta, permanently skewing split percents | resize | Inherited | Yes (still present) | beads `a6cc261` | Fixed |
| forge-h6z9 | keyboard-resize debounce timer not scoped per-window/grab, stranding grabMode/initRect on focus change | resize | Self-inflicted | n/a (self-inflicted) | beads `028a9a8` | Fixed |
| 1517ee7 | Windows visually traveled/drifted during resize and snapped back on release | resize | Inherited | Partial | pre-beads `1517ee7` | Fixed |
| forge-lid6 | Malformed user stylesheet.css throws in ThemeManagerBase ctor and aborts extension enable() | theme | Inherited | Yes (still present) | beads `4406864` | Fixed |
| forge-8jks | patchCss stylesheet copy throws uncaught GError on unwritable dir, aborting enable() half-initialized | theme | Inherited | Yes (still present) | beads `e107185` | Fixed |
| forge-0h9k | patchCss dereferences null config stylesheet on read-only config dir, aborting enable() | theme | Inherited | Yes (still present) | beads `e107185` | Fixed |
| forge-wwn8 | Manually loaded stylesheet is never unloaded on extension disable(), leaking theme state | theme | Inherited | Yes (still present) | beads `b852687` | Fixed |
| c3f3433 | Theme parser crashed on CSS comments/@-rules that lack a selectors property | theme | Inherited | Yes (still present) | pre-beads `c3f3433` | Fixed |
| forge-mo27 | removeChild evicts the wrong sibling when a stale node's index is null (value-match vs identity-match) | tiling | Inherited | Yes (still present) | beads `23e5474` | Fixed |
| forge-3jx9 | kbd getter snapshots undefined keybindings, so allowDragDropTile throws and wedges every drag-drop tile | tiling | Self-inflicted | n/a (self-inflicted) | beads `535ced5` | Fixed |
| forge-nmdo | removeNode dereferences node.parentNode without a null guard, aborting cleanTree mid-cleanup | tiling | Inherited | Yes (still present) | beads `23e5474` | Fixed |
| forge-5qp1 | Stacked layout shows no header offset when tab decoration disabled (by-design full overlap) | tiling | Self-inflicted | n/a (self-inflicted) | beads `24770eb` | Fixed |
| forge-aydd | Windows can render past the work-area bottom/right edge (unclamped move + stacked overflow) | tiling | Inherited | Yes (still present) | beads `d9261b5` | Fixed |
| forge-w35r | Stacked/tabbed toggles do nothing (gated off) and stacked layout has no title bars | tiling | Unclear | Partial | beads `12845c8` | Fixed |
| forge-3hsv | insertChildPercent gives float-exempt dialogs a tiled share, corrupting sibling split percents | tiling | Self-inflicted | n/a (self-inflicted) | beads `9ba22bc` | Fixed |
| forge-2s37 | window-gap-size applied in raw physical px, so gaps visually halve at integer HiDPI while dpi-scaled bars/borders keep their size | tiling | Inherited | Yes (still present) | beads `a774188` | Fixed |
| forge-j9fo | swapPairs transfers GRAB_TILE to the drag-swap target and _grabCleanup never resets it, stranding the target out of tiling once te9o is fixed | tiling | Inherited | Yes (still present) | beads `1207861` | Fixed |
| forge-qxqb | tree.move edge-wrap (next===-1) returns early, skipping percent-reset epilogue: percent corruption + stuck single-child TABBED | tiling | Inherited | Yes (still present) | beads `5ed88b7` | Fixed |
| forge-mhje | auto-split preamble in trackWindow runs before _validWindow/existNodeWindow, dispatching spurious splits (phantom single-child CONs) | tiling | Inherited | Yes (still present) | beads `0b236ec` | Fixed |
| forge-vw0l | _reorientOnClose reorients the detached CON on collapse (feature dead) and misfires on FLOAT-window removal | tiling | Self-inflicted | n/a (self-inflicted) | beads `5ed88b7` | Fixed |
| forge-clsp | Split applies default-window-layout to pre-existing container when tree.split no-ops, turning monitor node TABBED | tiling | Self-inflicted | n/a (self-inflicted) | beads `0b236ec` | Fixed |
| forge-43zk | minimize/unminimize resolve the focused window, not the signal window, resetting the wrong container's percents | tiling | Inherited | Yes (still present) | beads `0d38d8c` | Fixed |
| forge-dyt2 | Lone tiled window's external maximize is preserved by the signal path but silently reverted by the next renderTree | tiling | Self-inflicted | n/a (self-inflicted) | beads `fa74c2f` | Fixed |
| forge-wf49 | Workspace-monocle heuristic misfires: flattens a user tabbed CON beside a loose window; stuck-in-monocle with a minimized sub-CON window | tiling | Self-inflicted | n/a (self-inflicted) | beads `53b6279` | Fixed |
| forge-ojwb | restoreLayoutGroups alleged to splice rebuilt CON at a stale insertIndex (disproven, not reproducible) | tiling | Self-inflicted | n/a (self-inflicted) | beads | Fixed |
| forge-zyx3 | next() parent-walk dereferences null parentNode when no WORKSPACE ancestor | tiling | Inherited | Yes (still present) | beads `c57ebd5` | Fixed |
| forge-9s8c | SnapLayoutMove break is nested inside if(focusNodeWindow), falling through into ShowTabDecorationToggle | tiling | Inherited | Yes (still present) | beads `73a51ee` | Fixed |
| forge-xom3 | sortedWindows snapshot not pruned mid-drag; _findNodeWindowAtPointer throws on destroyed window wrapper | tiling | Inherited | Yes (still present) | beads `8bd8656` | Fixed |
| a88562a | Drag-drop reset createCon/detachWindow flags on reassignable childNode instead of focusNodeWindow | tiling | Inherited | Yes (still present) | pre-beads `a88562a` | Fixed |
| d1eeb8a | tree._search() MODE case fell through to LAYOUT due to missing break, mismatching nodes | tiling | Inherited | Yes (still present) | pre-beads `d1eeb8a` | Fixed |
| 629dae8 | Fix node move/prepend at monitor edge, flatten nested single-child containers, skip float/min windows | tiling | Inherited | Yes (still present) | pre-beads `629dae8` | Fixed |
| 23e0a56 | removeChild left stale parentNode reference and rect setter crashed on null rect | tiling | Inherited | Yes (still present) | pre-beads `23e0a56` | Fixed |
| forge-98sa | removeWorkspace leaks per-monitor St.Bins on dynamic-workspace removal; only the workspace bin was detached | workspace | Inherited | Yes (still present) | beads `2dac071` | Fixed |
| forge-c2yp | workspace-removed handler throws on a finalized wrapper, permanently desyncing the ws-index scaffold | workspace | Self-inflicted | n/a (self-inflicted) | beads `9b6b895` | Fixed |
| forge-yyum | Sticky 'Always on Visible Workspace' tiled window is re-homed into the active workspace, churning layouts | workspace | Inherited | Yes (still present) | beads `e7c6b4e` | Fixed |
| forge-7c7o | window-added debounce wedges permanently when a window is finalized within the 200ms window | workspace | Inherited | Yes (still present) | beads `9489e37` | Fixed |
| forge-6pe | Overview drag-to-insert-workspace flattens nested tiling on shifted workspaces | workspace | Inherited | Yes (still present) | beads `8c45267` | Fixed |
| forge-gw2c | workspaces-reordered never rekeys index-keyed _workspaceSignals, stranding window-added handlers (signal/St.Bin leaks) | workspace | Self-inflicted | n/a (self-inflicted) | beads `9725fdd` | Fixed |
| forge-2jxz | _renumberWorkspaces signal-map rekey can overwrite an existing key on collision, losing signal IDs | workspace | Self-inflicted | n/a (self-inflicted) | beads `73a51ee` | Fixed |
| forge-2s5b | workspaces-reordered unhandled: index-keyed ws nodes go stale, new windows tile into wrong workspace | workspace | Inherited | Yes (still present) | beads `258c5b5` | Fixed |
| forge-ojew | workspace-removed splices subtree before re-home reconcile, stranding all windows if tree empties | workspace | Inherited | Yes (still present) | beads `094cbbd` | Fixed |
| forge-7bry | _containerFullyMigrates can throw on a disposed window during multi-workspace reconcile; use isWindowAlive guard | workspace | Self-inflicted | n/a (self-inflicted) | beads `9b6b895` | Fixed |
| 95a9e7f | Workspace tree node IDs not renumbered on workspace add/remove, orphaning windows | workspace | Inherited | Yes (still present) | pre-beads `95a9e7f` | Fixed |
| de1f3ea | Moving a window between workspaces reset siblings to equal sizes instead of preserving proportions | workspace | Inherited | Yes (still present) | pre-beads `de1f3ea` | Fixed |

## 3. Still-unfixed bugs

| Ref | Bug | Area | Origin | In upstream/main? | Status |
|---|---|---|---|---|---|
| #464 / forge-7ww | A grey/blank window appears when the extension is enabled | decoration | Inherited | Yes (still present) | Open |
| #176 / forge-uja | Contextual menus render under the tiling borders | decoration | Inherited | Yes (still present) | Open |
| #454 / forge-05l | Forge causes Steam hover menus to close immediately | focus | Inherited | Yes (still present) | In progress |
| #109 / forge-e85 | Window loses focus on click on Wayland with Desktop Icons NG extension | focus | Inherited | Yes (still present) | Open |
| #495 / forge-tl6 | Some keyboard shortcuts do not work properly on Fedora | keybinding | Inherited | Yes (still present) | Open |
| #466 / forge-fu2 | Keyboard problems occur when activating Forge | keybinding | Inherited | Yes (still present) | Open |
| #328 / forge-zrf | White screen of death from finalized-GObject signal-disconnect storm during cross-monitor drag | lifecycle | Inherited | Partial | In progress |
| #224 / forge-2lx | GNOME 44 + Alacritty on Wayland causes a crash | lifecycle | Inherited | Yes (still present) | Open |
| #427 / forge-vmx | App launches on the wrong/second monitor | multimonitor | Inherited | Yes (still present) | Open |
| #388 / forge-4cv | Some windows always tile on the primary monitor | multimonitor | Inherited | Yes (still present) | Open |
| #353 / forge-91s | Some apps always open only on the top external monitor instead of the focused one | multimonitor | Inherited | Yes (still present) | Open |
| #299 / forge-4dm | Windows always open on the secondary display instead of the active monitor | multimonitor | Inherited | Yes (still present) | Open |
| #351 / forge-wsc | Window resizing lags when Brave shows popups | resize | Inherited | Yes (still present) | In progress |
| #260 / forge-iaj | Blender does not resize properly when launched | resize | Inherited | Yes (still present) | Open |
| #196 / forge-av4 | Window resize via gnome-resize is being ignored | resize | Inherited | Yes (still present) | Open |
| #531 / forge-cuv | Forge fails to tile windows at all in some environments | tiling | Inherited | Yes (still present) | Open |
| #514 / forge-bj4 | Incompatible with WPS Office windows (not tiled correctly) | tiling | Inherited | Yes (still present) | Open |
| #480 / forge-91r | Tiling does not work with Brave browser windows | tiling | Inherited | Yes (still present) | Open |
| #404 / forge-5r4 | VS Code not tiled when its window title starts with '+' | tiling | Inherited | Yes (still present) | Open |
| #354 / forge-tyt | Windows mis-swap when swapping with the mouse | tiling | Inherited | Yes (still present) | In progress |
| #324 / forge-ne1 | Crash when moving windows: Move's queued callback dereferences stale/dead nodes | tiling | Inherited | Partial | In progress |
| #288 / forge-bq3 | Conflict with GNOME default auto-maximize behavior | tiling | Inherited | Yes (still present) | Open |
| #254 / forge-efp | Qt5/6 windows get messed up when tiling (X11 only) | tiling | Inherited | Yes (still present) | Open |
| #213 / forge-zps | Moving windows via keyboard shortcuts is janky | tiling | Inherited | Yes (still present) | Open |
| #151 / forge-2iw | Drag-and-drop tiling does not work with touchscreen or stylus | tiling | Inherited | Yes (still present) | In progress |
| forge-fuce | Rare St.BoxLayout already-disposed crash in tabbed tab-teardown under fuzzer (bomy/v2yz family) | decoration | Self-inflicted | n/a (self-inflicted) | Open |
| forge-pvxj | Wayland window-toggle-float toggles both windows of the same multi-window app | float | Inherited | Yes (still present) | Open |
| forge-on7h | Evolution and non-snap Firefox windows always float instead of tiling | float | Inherited | Yes (still present) | Open |
| forge-2l83 | FloatOverride add/remove compare wmClass with strict === while classification uses comma-list match, so comma-list rules (Steam) can never be toggled off | float | Self-inflicted | n/a (self-inflicted) | Open |
| forge-xgrn | FloatClassToggle collaterally deletes other windows' per-window tile overrides and permanently shadows bundled class tile rules | float | Self-inflicted | n/a (self-inflicted) | Deferred |
| forge-lx9m | Bundled classless Picture-in-Picture float rule matches any window by title substring and beats class tile rules | float | Self-inflicted | n/a (self-inflicted) | Deferred |
| forge-3scn | Anki / Opera-flatpak never tile because null get_wm_class() forces the window to float | float | Inherited | Yes (still present) | Open |
| forge-85ex | No monitors-changed handling: hot-plugged monitor has no MONITOR nodes, breaking tiling/move | multimonitor | Inherited | Yes (still present) | Deferred |
| forge-162k | Chrome 149 windows cannot join an existing Forge tabbed container via drag-drop | tiling | Inherited | Yes (still present) | Open |

## 3b. Closed as not-a-defect / duplicate

| Ref | Bug | Area | Origin | In upstream/main? | Fixed in | Status |
|---|---|---|---|---|---|---|
| #289 / forge-b3p | Always-on-top windows conflict with fullscreen; headline symptom is by design | float | Inherited | Yes (still present) | both (pre `5e5e28d`, bd `?`) | Not a defect |
| forge-f5sl | Keyboard accel map.to() never returns false, so invalid shortcuts still toast 'Saved' | keybinding | Inherited | Yes (still present) | beads `69117d5` | Not a defect |
| forge-9fwj | Keyboard-resize debounce can strand grabMode/initRect on original window when focus is stolen externally | resize | Inherited | Yes (still present) | beads `cc27b2d` | Not a defect |
| forge-t3x5 | Suspected reorder of non-contiguous stacked cohort on reload; verified restoreLayoutGroups is correct | tiling | Self-inflicted | n/a (self-inflicted) | beads `a3f993f` | Not a defect |

## Appendix — test / CI / E2E infrastructure

| Ref | Bug | Area | Origin | In upstream/main? | Fixed in | Status |
|---|---|---|---|---|---|---|
| #125 / forge-mlpf | e2e TestBug125 stacked-layout gate timed out because the test never enabled stacked-tiling-mode | e2e | Inherited | Yes (still present) | both (pre `1a9aff3`, bd `2ce5be7`) | Fixed |
| #383 | Add regression/behavior tests covering prior bug fixes | e2e | Inherited | Yes (still present) | pre-beads `0d53472` | Fixed |
| forge-07x | Meta.Window mock lacked Mutter 49+ maximize methods (is_maximized/set_maximize_flags) | build | Self-inflicted | n/a (self-inflicted) | beads `724434d` | Fixed |
| forge-2xt | F40 E2E image: user@1000.service PAM failure prevents GNOME Shell boot | build | Self-inflicted | n/a (self-inflicted) | beads `a4851a9` | Fixed |
| forge-5tiz | dist payload ships dev config files (vitest.config.js, eslint.config.js) added by the fork | build | Self-inflicted | n/a (self-inflicted) | beads `f29d295` | Fixed |
| forge-q0k | E2E version-conditional xfailed/xpassed counts caused by a stale F44 image (build provenance) | build | Self-inflicted | n/a (self-inflicted) | beads `1c31ed7` | Fixed |
| 511105a | E2E Dockerfile missing build deps for dbus-python | build | Self-inflicted | n/a (self-inflicted) | pre-beads `511105a` | Fixed |
| bd12c3c | Documentation pass: annotate known limitations and won't-fix items in code comments | build | Inherited | Yes (still present) | pre-beads `bd12c3c` | Fixed |
| forge-my4w | E2E flake: two-window tests lose their 2nd window on the CI F42 lane (launch-race family) | e2e | Self-inflicted | n/a (self-inflicted) | beads `ad14e50` | Open |
| forge-1gjh | E2E sessions lack XDG_CURRENT_DESKTOP so GNOME default gsettings never apply, gating a non-default config | e2e | Self-inflicted | n/a (self-inflicted) | beads `7fd35de` | Fixed |
| forge-0a7t | E2E harness SIGABRTs in g_settings_get_value on GNOME 50 / Fedora 44 (Python 3.14), aborting the run | e2e | Self-inflicted | n/a (self-inflicted) | beads | Open |
| forge-v9o7 | E2E drag lane is vacuous: synthetic drags never fire grab-op-begin in headless containers | e2e | Self-inflicted | n/a (self-inflicted) | beads `a9b6e0f` | Deferred |
| forge-4b6 | drag_drop grab-ops contaminate the DBUS full-suite E2E lane on Mutter 45-48 | e2e | Self-inflicted | n/a (self-inflicted) | beads `5c00525` | Fixed |
| forge-8iw | E2E test_gap_keybinding leaks window-gap-size-increment via faulty setting restore | e2e | Self-inflicted | n/a (self-inflicted) | beads `4d4fda3` | Fixed |
| forge-0gj | gnome-text-editor GApplication launch race contaminates the full E2E lane | e2e | Self-inflicted | n/a (self-inflicted) | beads `34e18d7` | Fixed |
| forge-qh2 | E2E close-rebalance + post-toggle tests fail under dispatch-mode=dbus on F43/F44 | e2e | Self-inflicted | n/a (self-inflicted) | beads `3aee391` | Fixed |
| forge-27y | Migrate 101 fixed time.sleep() E2E calls to deterministic polling helpers | e2e | Self-inflicted | n/a (self-inflicted) | beads `3f241e7` | Fixed |
| forge-fc6 | Alleged ~100ms move_resize_frame apply delay disproven as cause of E2E close-rebalance failures | e2e | Self-inflicted | n/a (self-inflicted) | beads `3aee391` | Not a defect |
| forge-l7ms | E2E full-lane order-dependent failures: Bug125 stacked-toggle no-op + missing split border, deterministic under full 133-test ordering | e2e | Self-inflicted | n/a (self-inflicted) | beads | Open |
| forge-qwr | E2E stacked-toggle test fails on F42/GNOME48 (stacked-tiling-mode not enabled in test) | e2e | Self-inflicted | n/a (self-inflicted) | beads | Fixed |
| forge-2n0 | E2E keyboard-resize tests fail in full suite when Overview is hidden (focus not activated) | e2e | Self-inflicted | n/a (self-inflicted) | beads `ad16903` | Fixed |
| forge-g14 | E2E shell_proxy.is_window_floating() always returns True due to a broken tree root walk | e2e | Self-inflicted | n/a (self-inflicted) | beads `57b888b` | Fixed |
| forge-4wl | E2E F44/GNOME50 first-window cold-start launch flake (gnome-text-editor did not appear) | e2e | Self-inflicted | n/a (self-inflicted) | beads `ad14e50` | In progress |
| forge-5qh | Design a contamination-safe gating --dispatch-mode keybinding E2E CI lane | e2e | Self-inflicted | n/a (self-inflicted) | beads `1c31ed7` | Fixed |
| forge-6y7 | E2E Wayland failure-screenshot capture broken (gnome-screenshot missing), hangs/loses diagnostics | e2e | Self-inflicted | n/a (self-inflicted) | beads `1ba6382` | Fixed |
| forge-ehq | Add --dispatch-mode keybinding E2E CI lane (super+c keypress path had zero coverage) | e2e | Self-inflicted | n/a (self-inflicted) | beads `b66f8f8` | Fixed |
| forge-7vu | E2E run-tests.sh crash-check uses pgrep (absent in image), false gnome-shell-crashed warning each lane | e2e | Self-inflicted | n/a (self-inflicted) | beads `7ee5a02` | Fixed |
| forge-6et | Triage 8 in-body pytest.skip() calls in test_drag_drop_tiling.py | e2e | Self-inflicted | n/a (self-inflicted) | beads `bb64442` | Fixed |
| forge-7u3 | Unit-test mock sever: globalSetup replaced global.Main.overview, forcing overview-visible focus test to skip | e2e | Self-inflicted | n/a (self-inflicted) | beads `7c08f58` | Fixed |
| forge-3xz | E2E suite contamination: leftover MONITOR.layout and Clutter-keypress state caused 13-test stuck-window failures | e2e | Inherited | Yes (still present) | beads `4494eae` | Fixed |
| df04d19 | E2E gnome-text-editor interaction flaky with no org.gtk.Actions GApplication-readiness probe | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `df04d19` | Fixed |
| 7939cb0 | E2E suite unstable on GNOME 50 / Fedora 44 | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `7939cb0` | Fixed |
| d5921ce | E2E teardown used pkill instead of gdbus Quit for gnome-text-editor | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `d5921ce` | Fixed |
| 436cdaa | E2E dbus-daemon/gnome-shell died with bootstrap exec; needed systemd-run to outlive it | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `436cdaa` | Fixed |
| b25b729 | E2E close-rebalance tests used fixed sleeps instead of polling | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `b25b729` | Fixed |
| eee9c98 | E2E screenshot directory permission error on bind mounts | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `eee9c98` | Fixed |
| 6e3ba08 | gnome-shell crashed during E2E; migrated to self-contained containers | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `6e3ba08` | Fixed |
| 1e8bb15 | Our WindowManager focus unit tests failed due to missing Clutter backend and overview mocks | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `1e8bb15` | Fixed |
| 51125e9 | Our unit test infra broken by circular dependency and GObject.Object naming conflict | e2e | Self-inflicted | n/a (self-inflicted) | pre-beads `51125e9` | Fixed |

## Self-inflicted regressions (detail)

Bugs whose buggy code our own commits introduced, then fixed:

- **forge-0rb6** — Cheatsheet overlay has no reliable dismiss path (Escape/click-outside/close-X all missing) _(evidence: Cheatsheet is a fork-only feature: lib/extension/cheatsheet.js exists on dev, absent from upstream/main (no cheatsheet file or references). The unclosable-overlay bug is in our code.)_
- **forge-k5m6** — Cheatsheet overlay centered once at show() and never re-positioned on monitor/resolution change _(evidence: Cheatsheet is a fork-only feature: lib/extension/cheatsheet.js exists in dev but not in upstream/main (git ls-tree). Fixes aa6d3a4, 9f3cef1.)_
- **forge-v3y3** — Cheatsheet.show() re-adds an already-parented overlay (Clutter double-parent) during the hide ease _(evidence: Cheatsheet is a fork-only feature (cheatsheet.js absent from upstream/main). Double-parent bug is in fork code. Fix 9f3cef1.)_
- **forge-3t3a** — importAll() re-entrantly schedules exportAll(), rewriting the file just imported (no in-flight guard) _(evidence: Portable config-sync (importAll/exportAll, ConfigReload) is fork-only: lib/shared/config-sync.js and lib/prefs/portability.js absent from upstream; config-file-sync setting not in upstream gschema. Re-entrant export bug is in our code.)_
- **forge-orrf** — init() force-re-enables config-file-sync on every startup, overriding a user who disabled auto-sync _(evidence: config-file-sync-enabled and the init() startup-sync logic are fork-only (config-sync.js/portability.js absent upstream; setting absent from upstream gschema). The force-re-enable on startup is our code.)_
- **forge-el01** — 'Auto-sync changes' toggle ignored at runtime; auto-export cannot be turned off without restart _(evidence: The Auto-sync toggle (config-file-sync-enabled) and runtime auto-export are part of the fork-only config-sync feature, absent from upstream. The ignored-at-runtime bug is in our code.)_
- **forge-x55z** — Docs/schema claim wmClass rules use substring matching but code is exact per-comma-token equality, so partial-class rules silently never match _(evidence: Both drifted doc surfaces are ours: config/windows.schema.json and docs/user/rules.md do not exist in upstream/main; the 'substring' wording that contradicts our exact-match matcher (07b8919, also ours) was authored in our fork.)_
- **forge-nuny** — config-sync whitelists are stale, silently dropping 4 settings + 5 keybindings on export/import and rejecting them as schema-invalid _(evidence: lib/shared/config-sync.js does not exist in upstream/main; the portable-config export/import subsystem and its stale whitelists are entirely our fork's code.)_
- **forge-rt10** — config-sync auto-export resurrects a user-deleted portable file when only one of the two was deleted _(evidence: )_
- **forge-nn0m** — Prefs Import/Export and the extension's debounced exportAll clobber the same JSON with no coordination _(evidence: Coordination is between prefs Import/Export and the debounced exportAll auto-sync; exportAll/config-file-sync do not exist in upstream (git grep upstream/main: none). Entirely a fork feature. Fix 19216e2.)_
- **forge-qj5n** — Auto-export silently resurrects portable config files the user deliberately deleted _(evidence: Auto-export/config-file-sync is a fork-only feature (no exportAll/config-file-sync in upstream/main). Fix 5b888c9 guards on hasPortableConfig().)_
- **forge-v2yz** — use-after-dispose: _destroyDecoration leaves child .tab dangling, crashing on close in stacked/tabbed _(evidence: _destroyDecoration (whose missing _resetTabForReparent loop creates dangling .tab refs) is absent from upstream/main tree.js (count=0). The reset/teardown machinery is a fork addition (a3f993f/2b01d6a).)_
- **forge-ogmd** — Decoration self-heal catch nulls node.decoration without destroying the orphaned St.BoxLayout _(evidence: The process*/decoration self-heal catch that nulls node.decoration was authored by our fork's stacked/tabbed rewrite (12845c8); upstream/main processStacked/processTabbed have only empty catches and never null decoration, and removeChild destroys it properly. Fix 23e5474.)_
- **forge-5r0j** — Vacuous _destroyed guard on tab actors risks finalized-actor throw in nested tabbed churn _(evidence: The _destroyed guard on tab actors was added by our fork (1966856); upstream/main tree.js has no _destroyed flag at all, so the vacuous guard is fork-only code. Fix 23e5474.)_
- **forge-s7qo** — processTabbed error recovery nulls node.decoration but never recreates it, leaving an unhideable orphan _(evidence: The processTabbed error-recovery that nulls node.decoration without recreating it is fork-authored; upstream/main processTabbed has only empty catches and never nulls decoration. Fixes 2a20d34, 1938ee8, d8583b4.)_
- **forge-5l9b** — Queued raise-float event restacks a demoted float over a fullscreen window, permanently undoing float demotion _(evidence: Root cause fixed in 28dbe36 is our fullscreen float-demotion feature (_reconcileFullscreenFloatDemotion / _aboveDemotedForFullscreen, forge-zo4) which does not exist in upstream/main; the queued raise-float re-stacking the demoted float over fullscreen is a regression in our own added code (lib/extension/window.js). F40 legs were non-reproducible CI timing flakes.)_
- **forge-08he** — Dialogs permanently pinned always-on-top, so a sibling float can never be raised above them _(evidence: upstream `set float` only pins on floatAlwaysOnTop (tree.js:566); our commit 428bed8 added the isDialog forced make_above that strands popups. Fixed in 0159a15.)_
- **forge-jbkg** — Class-only tile override short-circuits floatByType heuristics, force-tiling that class's dialogs _(evidence: The tile-override feature (addTileOverride/mode 'tile') was added by our fork (b6f5e51, forge-fxf #387); upstream/main has no tile-override support (git grep: none, isFloatingExempt has zero tile handling). Fix b8177a1 adds specificity tracking.)_
- **forge-ph7f** — Rapid focus navigation strands windows always-on-top and un-tiles them into overlap on Wayland _(evidence: upstream focus() (tree.js:788) only raise/focus/activate — no make_above pin or _waylandStackingTimeoutId; the single shared Wayland stacking timer was added in our commit 19e00af, fixed in 3214290.)_
- **forge-jnfk** — Missing GLib import in tree.js makes Wayland directional focus throw, leaving windows permanently floating _(evidence: upstream tree.js has no GLib import and no make_above/GLib.timeout in focus(); the Wayland stacking pin using GLib.timeout_add was added by our fork without importing GLib. Fixed in 9489e37.)_
- **forge-u7t0** — Cheatsheet calls get_strv() on string-typed mod-mask-mouse-tile, logging one GLib CRITICAL per open _(evidence: lib/extension/cheatsheet.js does not exist in upstream/main; the whole cheatsheet feature (and its get_strv-on-string-key loop) is our fork's addition.)_
- **forge-rj4x** — media-keys GSettings override can hard-abort gnome-shell when a schema/key is absent _(evidence: SETTINGS_OVERRIDES (GNOME media-keys/Super+L override mechanism) is fork-only - not present in upstream extension.js. The unguarded Gio.Settings construction that hard-aborts gnome-shell on minimal installs is our code.)_
- **forge-606o** — _workspaceChangingTimeoutId never cleared in _removeSignals: 300ms timer outlives disable() _(evidence: _workspaceChangingTimeoutId absent in upstream; introduced by our fork commit 19e00af (refactor, NOT in upstream/main), so the uncleared-timer leak is in code we added.)_
- **forge-16ms** — Windows never tile on non-primary monitors under GNOME default workspaces-only-on-primary=true _(evidence: isFloatingExempt's is_on_all_workspaces()/floatByRole check was added by OUR commit 86b82e7 (forge-yyum), NOT in upstream/main. Upstream isFloatingExempt (window.js:2775-2827) has no such check. Regression created by our fork.)_
- **forge-w3ss** — SpinButtonRow bind and onChange are mutually exclusive, so Border radius/Tab margin CSS never updates _(evidence: upstream appearance.js wires Border radius via init+onChange (works), while our fork switched those rows to bind+onChange (appearance.js:152/160 pre-fix) which the bind-XOR-onChange widget silently drops. Commit msg: 'Regression vs upstream'. Fixed 7e555d1.)_
- **forge-3qj3** — EntryRow debounce timeout never cancelled on teardown; save() fires on a finalized prefs widget _(evidence: Upstream EntryRow saves synchronously on 'changed' with no timeout/teardown. The 1s debounce was added by our commit 76d65ee (not an ancestor of upstream); its uncancelled timeout firing on a finalized widget is our regression. Fix a1f5969 cancels in vfunc_unroot.)_
- **forge-l64o** — monitor-skip-tile missing from the settings-changed switch, so 'Non-tiling monitors' prefs edits do nothing until an unrelated render _(evidence: The monitor-skip-tile gschema key does not exist anywhere in upstream/main; it is our fork's feature. Upstream has only the workspace-skip-tile case in the settings-changed switch, so the omitted monitor-skip-tile case is a gap in our own added code.)_
- **forge-gm0z** — WindowExpand/Shrink fired four overlapping resize grabs that clobbered grabOp, so window never grew vertically _(evidence: WindowExpand/WindowShrink commands do not exist in upstream/main (git show upstream/main:lib/extension/window.js | grep -c WindowExpand = 0); they were authored by our commit fb84f7d and the 4-overlapping-grabs bug was in that code, fixed in 9ba22bc.)_
- **forge-ue92** — _grabCleanup re-walks post-reparent ancestors, stranding stale initRect on tabbed container after drag-out; next tab resize jumps _(evidence: The tabbed/stacked-ancestor initRect snapshot re-walk in _grabCleanup was introduced by our commit 06d073a (fix(resize) forge-pak, #497). Upstream window.js _grabCleanup has no tabbedAncestor/initRect walk at all. The post-reparent stale-initRect bug can only exist in our fork. Fix 69e6863.)_
- **forge-h6z9** — keyboard-resize debounce timer not scoped per-window/grab, stranding grabMode/initRect on focus change _(evidence: _manualResizeEndId absent in upstream (count 0); introduced by our fork commit 0776db7 (forge-5v6/#532 held-resize), so the unscoped debounce is a regression in code we authored.)_
- **forge-3jx9** — kbd getter snapshots undefined keybindings, so allowDragDropTile throws and wedges every drag-drop tile _(evidence: upstream get kbd() lazily constructs Keybindings (window.js:872-878) so an undefined snapshot self-heals; our refactor 19e00af removed the lazy init leaving `return this._kbd;`, which froze undefined. Fixed in 535ced5.)_
- **forge-5qp1** — Stacked layout shows no header offset when tab decoration disabled (by-design full overlap) _(evidence: )_
- **forge-3hsv** — insertChildPercent gives float-exempt dialogs a tiled share, corrupting sibling split percents _(evidence: insertChildPercent and its unconditional trackWindow call were introduced by fork commit 8c45267 (forge-7m3); git grep finds neither in upstream/main)_
- **forge-vw0l** — _reorientOnClose reorients the detached CON on collapse (feature dead) and misfires on FLOAT-window removal _(evidence: _reorientOnClose and auto-reorient-on-close are our feature, added by commit 8536f61 (feat(tree) forge-nl8). Upstream removeNode() has no _reorientOnClose call. The wrong-node reorient (detached CON) and FLOAT-removal misfire can only exist in the fork. Fix 5ed88b7.)_
- **forge-clsp** — Split applies default-window-layout to pre-existing container when tree.split no-ops, turning monitor node TABBED _(evidence: applyDefaultLayoutToContainer and default-window-layout are our feature (added by 629a163 / module extraction 3296d59). Upstream's Split command just calls tree.split() with no default-layout stamp. The no-op-split-turns-monitor-TABBED bug can only exist in the fork. Fix 0b236ec makes tree.split return the created CON and gates the stamp on it.)_
- **forge-dyt2** — Lone tiled window's external maximize is preserved by the signal path but silently reverted by the next renderTree _(evidence: The silent-revert disagreement exists only because our _shouldRejectExternalMaximize lone-tile exemption (added by aedc184 forge-9yo, fork-only; 0 occurrences upstream) preserves the maximize at signal time while tree.apply/move still unmaximizes on render. Upstream move() always unmaximizes and apply() re-slices every tiled window unconditionally (consistent, no exemption), so upstream has no such disagreement. Fix fa74c2f adds _isLoneMaximizedTile skip in tree.apply.)_
- **forge-wf49** — Workspace-monocle heuristic misfires: flattens a user tabbed CON beside a loose window; stuck-in-monocle with a minimized sub-CON window _(evidence: toggleWorkspaceMonocle/isMonocle do not exist in upstream/main (grep returns nothing); introduced by our fork commit 629a163 'Implement 4 features: #435, #414, #287, #398' in upstream/main..dev. Fork-authored feature, so the buggy heuristic is our own.)_
- **forge-ojwb** — restoreLayoutGroups alleged to splice rebuilt CON at a stale insertIndex (disproven, not reproducible) _(evidence: )_
- **forge-c2yp** — workspace-removed handler throws on a finalized wrapper, permanently desyncing the ws-index scaffold _(evidence: _rehomeWorkspaceWindowsBeforeRemoval/_rehomeWindowToLiveLocation/_containerFullyMigrates absent from upstream. Upstream workspace-removed handler (window.js:268-273) is a trivial removeWorkspace+renderTree with no dead-node rehome walk. Throwing code is fork-authored.)_
- **forge-gw2c** — workspaces-reordered never rekeys index-keyed _workspaceSignals, stranding window-added handlers (signal/St.Bin leaks) _(evidence: The index-keyed `_workspaceSignals = new Map()` WorkspaceManager and the workspaces-reordered rekey are our refactor (workspace.js added by commit 3296d59, in upstream/main..dev). Upstream has no workspace.js: it attaches signals directly to the workspace object (metaWorkspace.workspaceSignals) and never listens to workspaces-reordered, so it has no index-desync bug. Fix 9725fdd.)_
- **forge-2jxz** — _renumberWorkspaces signal-map rekey can overwrite an existing key on collision, losing signal IDs _(evidence: _renumberWorkspaces is fork-only: absent from upstream lib/extension (no workspace.js, no 'renumber' anywhere in upstream); added by our commit 19e00af; related to fork fix forge-6pe.)_
- **forge-7bry** — _containerFullyMigrates can throw on a disposed window during multi-workspace reconcile; use isWindowAlive guard _(evidence: _containerFullyMigrates and _queueWindowHomeReconcile are fork-only (0 matches in upstream/main window.js); fix bf04456 switches the predicate to Utils.isWindowAlive.)_
