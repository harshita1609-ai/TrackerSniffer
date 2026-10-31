# TrackerSniffer
A privacy-focused Chrome extension that audits observed third-party tracking activity, identifies known trackers, inspects cookie metadata, and generates an easy-to-understand privacy scorecard.
TrackerSniffer --- Third-Party Ad & Cookie Audit Extension
TrackerSniffer is a privacy-focused Chrome extension project designed to
help users understand the third-party tracking activity observed while
they visit a website. It aims to identify external domains, compare them
with a locally stored tracker catalogue, inspect accessible cookie
metadata, and present the findings in a clear privacy scorecard.
Project status: In development. Features described below are the
intended project scope and may not all be implemented yet.

# Table of Contents
- Project Goals
- Planned Features
- How It Works
- Technology Stack
- Privacy by Design
- Privacy Score
- Getting Started
- Planned Project Structure
- Testing
- Known Limitations
- Roadmap
- Team
Project Goals
TrackerSniffer explores the question:
Can a Chrome extension use observed resource domains, accessible
cookie metadata, and a curated tracker list to give users an
understandable summary of third-party tracking activity?
The project is intended for privacy-conscious users, cybersecurity
learners, website developers, and people auditing website resources.
Planned Features
- Observe eligible network requests for the active website using
  supported Chrome extension APIs.
  Extract and normalize hostnames from observed resource URLs.
Distinguish first-party and third-party domains using documented
domain-comparison rules.
- Inspect accessible cookie metadata, such as cookie domain and
  security attributes.
- Match observed domains against a local tracker catalogue.
- Categorize recognized trackers, such as advertising, analytics, and
  social media.
- Display unique observed domains, recognized trackers, and cookie
  statistics in a simple dashboard.
- Calculate a project-defined privacy score from 0--100 and map it to
  a grade from A--F.
- Clearly label unknown domains and incomplete or unsupported audits.
- Potential future additions: CSV export, rescan controls, website
  comparisons, and sector-level analysis.
How It Works
1. Observe: Collect eligible request metadata during a defined
   audit window.
2. Extract: Parse request URLs and normalize hostnames.
3. Classify: Determine first-party, third-party, or uncertain
   status using documented rules.
4. Match: Compare domains against a versioned local tracker
   catalogue.
5. Summarize: Count recognized trackers and accessible cookie
   metadata.
6. Report: Show the findings and explain the limitations of the
   scorecard.
A third-party domain is not automatically a tracker. Domains that do not
match the catalogue should remain unknown, rather than being
labelled safe.
Technology Stack
  Component                           Planned technology
  Browser extension                   Chrome Extension Manifest V3
  Interface                           HTML, CSS, JavaScript
  Network observation                 Supported Chrome extension request
                                      APIs, such as chrome.webRequest
                                      where appropriate
  Cookie metadata                     chrome.cookies API
  Tracker catalogue                   Local JSON dataset
  URL and hostname parsing            JavaScript URL API and
                                      domain-aware matching
  Charts                              Chart.js (optional)
  Data analysis                       Python 3, pandas, and matplotlib
                                      (stretch goal)
  Version control                     Git and GitHub
The exact API configuration and permissions will depend on the supported
Chrome version and audit requirements. declarativeNetRequest is
intended for request rules and is not a general-purpose network request
logging API.
Privacy by Design
TrackerSniffer is designed for auditing, not surveillance or
blocking.
- Analyze only the active website and the resources observable within
  the audit window.
- Request only the browser permissions needed for the selected
  functionality.
- Do not collect or store cookie values, passwords, session
  tokens, or personal form data.
- Avoid retaining full request URLs when hostnames are sufficient.
- Keep analysis local by default; do not transmit browsing history to
  a remote server.
- Explain why permissions are requested and what information is
  inspected.
- Report inaccessible data or incomplete scans honestly.
Privacy Score
The planned score ranges from 0 to 100, with these project-defined
grade bands:
  Score  Grade  Interpretation
90--100    A    Low observed tracking activity under this model
 80--89    B    Relatively low observed activity
 65--79    C    Moderate observed activity
 50--64    D    Elevated observed activity
  0--49    F    High observed activity under this model
Important: These thresholds are a project heuristic, not an official
privacy certification. The scoring formula and any weights must be
documented before results are interpreted. A score is not a measure of
overall website safety, trustworthiness, or legal compliance.
Getting Started
The repository is being developed. Once the initial extension files are
committed, the intended local setup is:
1. Clone or download this repository.
2. Open Google Chrome and navigate to chrome://extensions.
3. Enable Developer mode.
4. Select Load unpacked.
5. Choose the project directory containing manifest.json.
6. Open a supported website, then open TrackerSniffer and run an audit
   if that feature is available in the current build.
Do not load the extension until a valid manifest.json and the required
source files have been added. The exact setup steps may change as
development progresses.
Planned Project Structure
TrackerSniffer/
├── manifest.json
├── popup.html
├── popup.css
├── popup.js
├── background.js
├── data/
│   └── tracker-list.json
├── scripts/
│   └── analysis.py
├── tests/
│   └── domain-matching-tests.md
└── README.md
This is a suggested structure and may change during implementation.
Include only files that actually exist in the repository.
Testing
Planned test cases include:
- Known tracker domains and valid tracker subdomains.
- Ordinary external resources, such as CDNs, payment, and
  authentication services.
- First-party subdomains.
- Similar-looking but unrelated domains (for example, notexample.com
  must not match example.com).
- Missing or malformed URLs.
- Pages with no observed external resources.
- Delayed network requests and manual rescans.
- Restricted cookie access and unsupported pages.
- Score calculations, incomplete audits, and unknown domains.
Evaluation should document classification accuracy, false positives,
score calculations, and the conditions under which each audit was
performed.
Known Limitations
- Only eligible requests and accessible cookie metadata may be visible
  to the extension.
- Activity that occurs outside the audit window may not be captured.
- Consent choices, browser restrictions, dynamic content, and website
  behavior can affect results.
- The tracker catalogue may be incomplete or outdated.
- Unknown domains are not necessarily safe or malicious.
- Observed third-party activity does not, by itself, prove that
  personal information was collected.
- The grade summarizes observed activity according to this project's
  documented model; it is not a formal privacy or compliance
  assessment.
  
# Roadmap
- [ ] Set up the Manifest V3 extension skeleton and document
  permissions.
- [ ] Create and normalize a local tracker catalogue.
- [ ] Implement hostname extraction and domain-boundary matching.
- [ ] Add supported request observation and cookie metadata
  inspection.
- [ ] Implement documented first-party/third-party classification.
- [ ] Define and test the privacy scoring formula.
- [ ] Build the dashboard and clear no-data/unsupported states.
- [ ] Test false positives, incomplete audits, and domain edge cases.
- [ ] Document findings and prepare a project demonstration.
- [ ] Consider optional CSV export and sector analysis if time
  permits.


# Mentor
- Tanishka ma'am

# Team
- Harshita Singh
- Soumay Manderna
  

  
# Disclaimer
TrackerSniffer is an educational privacy-auditing project. It does not
automatically block trackers, guarantee detection of all tracking
activity, or provide a certified privacy assessment. Use it only on
websites you are authorized to inspect and follow applicable policies
and permissions.
