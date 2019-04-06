# REDCap Custom Footer

A REDCap External Module that allows system admins and project admins to add custom footers to REDCap pages (survey, project, and system pages).

## Purpose

This External Module was designed to allow REDCap administrators to add custom footers to any pages displayed by REDCap. The reasons for wanting or having to add custom footers are most likely due to regulatory requirements, such as e.g. conformance with General Data Protection Regulations (GDPR) or other legal requirements.

In the EU, for instance, on each page of a website *direct* access to imprint information and privacy policies has to be provided. Usually, this is only necessary on publicly exposed pages, which in most cases is limited to REDCap survey pages. In some circumstances, however, REDCap's "regular" user interface (system pages, data entry pages) may be exposed to outside parties, e.g. participating physicians/institutions in a register study, and the duty to provide the information mentioned above has to be fulfilled.

Since recently, REDCap provides *"Settings relating to Data Privacy (e.g., GDPR)"* on the *"Edit a Project's Settings"* page (accessible from *Control Center*). However, the facilites provided there do not cover all scenarios outlined above. Thus, this External Module tries to fill this gap, by providing the means to add custom footers (containing any required information or appropriate links) as a system setting, as well as to provide a means for individual projects to add to (or replace) the system settings (if the REDCap administrator chooses to allow this).

## Effect

Custom footer messages will be injected into REDCap pages depending on the page type:

- **Survey pages**: Under the "Powerd by REDCap" line. The complete footer will remain visible even on small screens.
- **Project pages**: In the menu sidebar on the left side, as a new section following *Help & Information*.
- **Other pages** (such as the login page or *Home* or *My Projects*): Under the REDCap version and copyright notice.

## Requirements

- REDCAP 8.1.0 or newer (tested with REDCap 8.11.7 on a system running PHP 7.0.33).

## Installation

- Clone this repo into `<redcap-root>/modules/redcap_custom_footer_v<version-number>`, or
- Obtain this module from the Consortium [REDCap Repo](https://redcap.vanderbilt.edu/consortium/modules/index.php) via the Control Center.
- Go to _Control Center > Technical / Developer Tools > External Modules_ and enable REDCap JavaScript Injector.

## Configuration

Configuration of this module is designed such that the REDCap administrator is in total control of the module's settings, including control over what project admins can do.

### System-Level Settings

After enabling the module, REDCap administrators should configure the module and activate the *"Enable module on all projects by default"* setting. The settings *"Make module discoverable by users"* (off) and *"Module configuration permissions in projects"* (Require Project Setup/Design privilege) should be left at their defaults.

- **Enabled on**
  Controls whether the custom footers set in the system settings should be disabled, or shown on all (*both*) or only specific (*Project / Data Entry Pages* or *Survey Pages*) pages.

- **Title for section in left side menu**:
  As there is no good place on REDCap pages that feature the left-side menu to inject a footer (the existing footer is very resilient to manipulations), this module will inject the custom footers in the menu area on such pages. Here, a title can be set for the added section. If left blank, no header section will be added to the added menu panel.

- **Custom footer for project / data entry pages**:
  Add any Text/HTML to be injected as footer in data entry pages.

- **Custom footer for survey pages**: Choice to use the same custom footer as for data entry pages or a different one.

As noted above, REDCap administrators will have full control over what project admins can do with regard to this module. System settings will apply to all projects (provided the option to automatically activate this module on all projects by default is activated, and the module has not subsequently been disabled in a project).

Note that superusers can always access the project configuration and disable this module for any project.

- **Allow project admins to configure settings**: The *Configure* button can be hidden for all projects or enabled for all or only selected projects. By default, project-specific configuration of the module is prohibited.

- **Allow override of system settings in projects**: Override means that project footers can replace the footers set on the system level. Otherwise, if custom footers are configured both on the system and project level, both will be shown simultaneously.

- **Position of custom project footers**: Determines the order in which system and project footers shown. If the previous setting allows project admins to override system footers, they can also change this order.

### Project-Level Settings

The first three settings (overrides) only take effect when specifically allowed by the REDCap administrator in the system settings of the module (see above).

- **Override system settings for project / data entry pages**: When enabled, the footer set at the system level for project / data entry pages will be overriden (i.e. only the footer specified in the project settings will be shown; if this footer is blank, no footer will be shown).

- **Override system settings for survey pages**: When enabled, the footer set at the system level for survey pages will be overriden (i.e. only the footer specified in the project settings will be shown; if this footer is blank, no footer will be shown).

- **Override footer position - show project footer**: Determines the order in which project and system footers are shown when both are enabled.

- **Enabled on**: Specifies on what type of pages (data entry and/or survey pages) the custom footer is shown.

- **Custom footer for project / data entry pages**:
  Add any Text/HTML to be injected as footer in data entry pages.

- **Custom footer for survey pages**: Choice to use the same custom footer as for data entry pages or a different one.