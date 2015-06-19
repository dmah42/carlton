# oapi/carlton
Project Carlton

Project Carlton allows users to track abuse they've received from any conceivable platform, creating individual and private 'case files' that can be easily viewed and downloaded. Additionally, this data would allow us to more easily track harassment patterns over different forms of online media.

Having never suffered online harassment I can't imagine why having an individual case file would be useful, but the ability to track harassment patterns and do things like live analysis of dogpiling or creation rate of abusive accounts will be powerful. Being able to generate reports per-platform of abuse should also help raise visibility to the platform owners of the issues.

## Planning Doc

### Goals

* Remove the need to keep screenshots of harassment.
* Securely store all logged abuse indefinitely in the cloud.
* Tag all stored harassment by platform as well as user issuing the harassment.
* Create one button PDF downloads based off of tags.
* Tie a single harasser's user accounts together across social networks.
* Track all harassment a single user has issued, and provide that data to law enforcement upon request.
* Create anonymized abuse metrics based on this data.
* Store all information required for law enforcement to create requests for data.
  * US law enforcement or global law enforcement?
* Provide documentation to law enforcement about user IP storage timelimits (when applicable) & how to request extensions from companies.
* Create direct tie-ins to many platforms (Twitter, Tumblr, Facebook, Google+, YouTube) that remove the need for screenshots.
  * would taking screenshots automatically work?

### Ingress Plugins

This is highly dependent on how much external buy-in we receive. All support should be done in plugin format, especially as we might run into issues of proprietary APIs that can't be open sourced.

* Chrome and Firefox plugins.
 * Look at storify for this. Their plugin even covers reddit.
 * https://github.com/niklasvh/html2canvas might work, except for cross-origin requests.
* Email ingress for forwarding abusive emails.
* Image upload: JPG, PNG, TIFF, BMP
* Facebook app
 * Can a facebook app allow us to tie in comments from a user's timeline?
* Twitter app
 * Ideas: user can DM a tweet to our abuse tracking bot, adding it to their case file.

### Account Data

* provide a method to delete an account & all data associated with it.
  * including abuser accounts if there's some abuse of the system and people are flagged incorrectly
* cold storage for older images. never delete without user request.
* privacy concerns
  * do we need to provide a way for users to opt out of anonymous metrics?
  * what about providing complete case files on an abuser to law enforcement?
  * anonymizing data sets is a tricky thing, especially with sensitive data. i contributed to [some research](http://www.oii.ox.ac.uk/research/Ethical_Privacy_Guidelines_for_Mobile_Connectivity_Measurements.pdf) on privacy and open data sets which might be interesting. 
  * specifically, it might be worth looking in to [Differential Privacy](https://en.wikipedia.org/wiki/Differential_privacy)

### Environment

* Google AppEngine
 * Benefits: DDoS protection, good security team, redundancy, backups
* Languages: python, go.
* License: BSD

### Security Concerns

* Authentication should be done via OAuth to Twitter, Facebook, Google. Users can link multiple social media accounts as login sources. Never keep passwords, only ever use OAuth.
* Do not accept PDF uploads.
* Use a transcode engine to make any image uploads safe.

### Volunteer Expertise

* Chrome plugins
* Firefox plugins
* Facebook App dev
* Google AppEngine with Python or Go
* Google AppEngine Datastore with Python
* Google Cold Storage with Python
* Experience designing modular/plugin based applications
