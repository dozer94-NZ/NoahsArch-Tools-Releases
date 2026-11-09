# NoahsArch Tools

Revit tools by Noah, for Revit 2024, 2025, 2026 and 2027. This release contains **NoFilter**: build, apply and save view filters and their graphics overrides from one floating window, instead of going through Filters and Visibility/Graphics dialogs.

**Download:** the latest `NoahsArch-Tools-Setup-<version>.exe` is under **Releases** on this page.

---

## Install

1. Close Revit.
2. Run `NoahsArch-Tools-Setup-<version>.exe`. No admin rights needed; it installs for your Windows account only.
3. Windows may show **"Windows protected your PC"**. That's because the installer isn't signed by a company certificate yet. Click **More info**, then **Run anyway**.
4. Click through the installer. It finds the Revit versions on your PC and installs for each.
5. Start Revit. The first time, Revit asks whether to load **NoahsArch Tools** from an unknown publisher: choose **Always Load**.

You'll find a **NoahsArch Tools** panel on Revit's **Add-Ins** tab with one button, **Noah's Arch** (the ark). Click it to open a tool, see your version and install updates.

## Updates

When there's a new version, the Noah's Arch button changes to **Update available**. Open the Hub and click **Update**. The update downloads and installs by itself as soon as you close Revit; start Revit again afterwards.

To remove NoahsArch Tools: Windows **Settings → Apps → Installed apps → NoahsArch Tools → Uninstall**.

---

## NoFilter

Open a project view (plan, section, 3D…), click **Noah's Arch** on the Add-Ins tab and choose **NoFilter**. The window floats next to Revit and follows the view you're in. It only works in projects, not in the family editor.

The window has three columns: **what to filter** on the left, **the rules** in the middle, **how it looks** on the right.

### 1. Pick categories (left, "New filter" tab)

- The list is Revit's own filter category list. Tick one or more categories.
- **Search** narrows the list as you type. **Filter list** narrows it to a discipline.
- **Only categories in this view** hides categories with nothing in the active view.
- **Use selection** ticks the categories of whatever you've selected in Revit.

### 2. Add rules (middle)

- The **Parameters** list shows the parameters all ticked categories share. Hover one to see values used in the model.
- **Drag** a parameter into the rules area, or **double-click** it.
- Choose a condition (equals, contains, is greater than, has a value…) and a value. The value box lists values found in the model; you can also type. Lengths work in project units ("200" or "200 mm").
- The **Reads as** line spells out your filter in plain words, with brackets.
- The big number shows **how many elements match** in the active view, live.

**AND / OR and groups**

- Click any **AND** / **OR** label to switch it.
- To mix AND and OR, group rules: drop a parameter on the dashed strip **under** a rule (or click **or pick from list** there, then double-click a parameter). The two become a lavender **group** with its own AND/OR.
- Example: *Width < 200 **AND** (Fire Rating = 60 **OR** Height > 1800)*. The group acts like the brackets.
- **Ungroup** splits a group back into single rules; **× Remove group** deletes it.
- Reorder with the **⠿** grip or **↑ / ↓**. Order doesn't change the result.
- Drag a rule onto another rule's strip to move it into that group, or onto the bottom drop zone to make it its own row.
- "Unless…" = use a **does not…** condition (does not equal, does not contain…).

### 3. Set the look (right)

- Quick presets: **Highlight red**, **Grey out**, **Hide**, **Clear**.
- **Your own presets:** set up a look, click **+ Save as preset** and give it a name. It appears as a lilac chip after the built-in four; click it to use it. Right-click it to **Update with current settings**, **Rename**, **Share to team folder** or **Delete**. Saving keeps everything except **Enable filter**.
- **Team presets:** looks shared by colleagues appear in a **TEAM** row underneath. Right-click one to copy it to your own presets.
- **Enable filter**, **Visible**, **Halftone**.
- Projection/surface and cut: line pattern, colour, weight; foreground and background patterns and colours; transparency.
- **Copy overrides from another filter…** takes the look from a filter already on the view.

### 4. Apply and save (bottom)

| Button | What happens |
|---|---|
| **Apply to view** | Puts the filter on the active view as a draft. Change things and apply again as often as you like. |
| **Save to project** | Keeps it as a normal Revit filter under the name at the top. |
| **Apply to view template ▾** | Adds it to view templates. The active view's template is listed first and ticked; tick others. It shows how many views will be affected. |
| **Apply to other views…** | Adds it to views you tick. Views controlled by a template are greyed out: use the template option for those. |
| **Discard draft** | Removes the draft from the view and resets everything (categories, searches, rules, look) so you can start fresh. |

- **Name:** filled in automatically from your rules (e.g. `DOOR_Width LT 200 AND (FireRating EQ 60 OR Height GT 1800)`). Type your own if you like; **Reset to auto** brings the automatic one back. Revit names can't contain `\ : { } [ ] | ; < > ? ` ~`.
- **Views with a template:** if the view's template controls filters, NoFilter applies to the view through **Temporary View Properties** (purple frame), so the template isn't changed. Use **Apply to view template** to change the template itself.
- New filters go to the **top** of the view's or template's filter list, so filters already there can't overrule them. The others keep their order underneath.
- Every action is one undo step in Revit, named "NoahsArch: NoFilter …".
- Closing NoFilter removes an unsaved draft.

**Select and isolate**

- **Select matches** selects the matching elements in Revit.
- **Isolate (temporary)** isolates them (Revit's Temporary Hide/Isolate). If nothing matches, everything is hidden. **Reset isolate** brings everything back.

### 5. Existing filters ("Project filters" tab)

- Lists every filter in the project; ones on the active view are marked **On view** and come first.
- **Click a filter** to load it into the builder. Then choose:
  - **Edit everywhere**: your changes update that filter in every view and template that uses it (the bar shows how many).
  - **Duplicate & edit**: work on a copy; the original stays as it is.
- Right-click a filter: **Remove from this view**, **Save as preset**.
- **Saved selections:** build rules, then click **Save as selection ▾ → New selection…** next to Select matches. It saves the rules (not the elements) to your profile. In the **Selections** tab, click one to select what matches now in **This view** or the **Whole model** (switch at the top); Ctrl+click adds to the selection. They work in every project. Team selections from the team folder are listed underneath; right-click one of yours and choose **Copy to team** to share it. Clicking a selection also shows its rules in the editor.
- **Selections with several parts:** one selection can combine different categories with different rules, e.g. doors with Type Mark X *and* walls with height Y. Build the walls rule, then **Save as selection ▾ → Add as a part to → sel_1** (or right-click sel_1 → **Add the editor's rules as a part**). Right-click to edit, remove or split parts.
- **Create schedule** (footer, or right-click a project filter): a schedule of the filter's categories with Family and Type, the rule parameters and Count. AND rules filter it; Revit schedules can't do OR, so a filter with OR gives everything in those categories, sorted. Several categories make a Multi-Category schedule grouped by category.
- **Several at once:** tick filters, then right-click any filter: **Remove ticked from this view**, **Remove ticked from view template…** (permanent, for every view using that template), **Save ticked as presets**, **Clear ticks**. Export ticked filters from **Import ▾**.
- Filters made in Revit with groups inside groups open with read-only rules; you can still change their look.

### 6. Import, presets and the team folder

**Import ▾** on the Project filters tab:

| Option | What it does |
|---|---|
| **From another view…** | Pick a view or template, tick its filters: they come onto this view with that view's look. |
| **From another open project…** | Copy filters from another model open in Revit. |
| **From my presets…** | Your own saved filters (`%APPDATA%\NoahsArch\FilterCanvas\presets`). |
| **From team folder…** | Your team's shared filters (below). |
| **From file…** | A `.json` file someone sent you. |
| **Save current as preset** | Saves the filter you're building (rules and look) to your presets. |
| **Share current to team folder** | Saves it to the shared team folder for everyone. |
| **Export ticked filters…** | Tick filters in the list, save them to one `.json` file. |

Before anything is imported you see a check list: what matched this project and what didn't (a missing parameter or line pattern is listed, not silently dropped). If a filter with the same name exists, choose **Import as copy**, **Use existing** or **Replace its rules**.

**The team folder (shared presets and selections)**

A team can share filters, looks and saved selections through one shared folder, for example a SharePoint library synced to each PC with OneDrive, or a network folder.

- Open **Settings** in NoFilter (or click **Set up…** on the banner the first time) and use **Browse…** next to **Team folder**. Each person does this once on their own PC.
- **My folder** in the same dialog is where your own presets and saved selections go. Leave it empty for the default, or pick a OneDrive folder to have them on every PC.
- Shared items then show in the **TEAM** rows. Sharing to the team needs write access to the folder.
- No folder set? Everything else works; the team rows stay empty.

---

## Something not working?

- **No NoahsArch Tools panel on the Add-Ins tab after installing:** close Revit completely (check the taskbar) and start it again. Revit loads add-ins at startup.
- **"This view can't have filters":** schedules, sheets and legends can't; switch to a plan, section, elevation or 3D view.
- **A rule shows "not available":** that parameter isn't shared by all ticked categories; untick the extra category or pick another parameter.
- Anything else: send Noah the version (shown in the Hub) and a screenshot.
