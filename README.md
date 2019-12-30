# 1. Access News

## 1. Overview

```text
######## BACK-END(S) ##############################  ### FRONT-ENDS ##############################
#                                                 #  #                                           #
# +--- CORE ------------------------------------+ #  # +--- PHONE SERVICE (TR2) ---------------+ #
# |                                             | #  # |                                       | #
# |  PURPOSE                                    | #  # |  Listeners only. [1]                  | #
# |  -----------------------------------------  | #  # |                                       | #
# |  Provides API and Websocket service         | #  # |  TECHNOLOGIES                         | #
# |  for front-ends to                          | #  # |  ------------------------------------ | #
# |                                             | #  # |  + FreeSWITCH (phone server)          | #
# |  + access/store audio content               | #  # |  + Erlang (application)               | #
# |                                             | #  # |                                       | #
# |  + aggregate listener and volunteer         | #  # |                                       | #
# |    stats and metrics                        | #  # |                                       | #
# |                                             | #  # |                                       | #
# |  TECHNOLOGIES                               | #  # +---------------------------------------+ #
# |  -----------------------------------------  | #  #                                           #
# |  + Phoenix (Elixir web framework)           | #  # +--- WEB APPS --------------------------+ #
# |                                             | #  # |                                       | #
# |  + PostgreSQL (database)                    | #  # |  PWAs (progressive web apps)          | #
# |                                             | #  # |                                       | #
# |  + storage? (file system? Azure blobs?)     | #  # |  TECHNOLOGIES                         | #
# |                                             | #  # |  ------------------------------------ | #
# +---------------------------------------------+ #  # |  HTML, CSS, JavaScript, ? [2]         | #
#                                                 #  # |                                       | #
# +--(Else?) -----------------------------------+ #  # +---------------------------------------+ #
# |                                             | #  #                                           #
# |                                             | #  # +-- MOBILE APPS ------------------------+ #
# |                                             | #  # |                                       | #
# +---------------------------------------------+ #  # | +--- ANDROID ---+  +--- iOS --------+ | #
#                                                 #  # | |               |  |                | | #
###################################################  # | | Java,         |  |  Swift,        | | #
                                                     # | | Kotlin        |  |  Objective-C   | | #
###################################################### | |               |  |                | | #
#                                                      | |          +-------------+          | | #
#   +--- OTHERS -------------------------------------+ | |          | PWAs? [3]   |          | | #
#   |                                                | | |          +-------------+          | | #
#   |                                                | | |               |  |                | | #
#   |  * Alexa Skills (Amazon)                       | | +---------------+  +----------------+ | #
#   |  * Google Assistant Actions                    | +---------------------------------------+ #
#   |  * Victor Reader                               |                                           #
#   |  * Apple services (?)                          |                                           #
#   |  * ... else?                                   |                                           #
#   +------------------------------------------------+                                           #
##################################################################################################
```

[1] The   legacy   phone   service  provided   recording
    capabilities (in fact, that  was the main method for
    volunteers)  but the  audio quality  over the  phone
    always depends  on the lowest quality  connects, and
    thus it was mostly very bad.

[2] The question  mark is to  emphasize **exploration**.
    See **3. Technology choices** section below.

[3] [**Progressive web apps**](https://developers.google.com/web/progressive-web-apps)
    (PWAs) can be installed as standalone applications on Android, and
    [soon on iOS as well](https://medium.com/@firt/progressive-web-apps-on-ios-are-here-d00430dee3a7).

    The main goal  is for the new apps  to be accessible
    though, and not sure how PWAs hold up in this aspect
    against native apps.

## 2. Social aspects

The notion is to  make Access News more interactive,
making it possible for both volunteers and listeners
(referred to  as users  from now on)  to be  able to
shape the service directly.

> There  are obvious  issues with  meritocratic models
> (e.g., Stackoverflow). What would be a better one?

This means that  each user will be  granted a custom
set  of permission  to complete  certain tasks.  For
example, some will be able to

+ edit audio files (proof-listeners)
+ edit content metadata
+ moderate comments and discussions
+ prepare scraped articles to be read
+ respond (and fulfil) requests (i.e., by adding new
  content or re-structuring a category, etc.)
+ (what else?)

and combinations of the above.

As  a  corollary  of  listeners  being  included  as
"users"  is that  **all  parts  of the  applications
need  to  be  accessible**.  For  example,  a  blind
proof-listener has  to be  able to edit  audio files
when necessary.

## 3. Technology choices

### 3.1 Goals (or "mission statement"?)

Long-term goals are of higher importance than having
the  apps  delivered  quickly. **The  notion  is  to
become a community that supports and is accomodating
towards   individuals  of   all  skill   levels  and
abilities**.

The way this pertains to choices in the technologies
used   is  that   **diversity  is   welcomed**,  and
**experimentation/exploration  is  encouraged**.  It
is  sure  easier to  write  an  app using  the  same
framework/language/editor/operating sytstem/etc. all
the time,  but this project  is also for  having the
liberty of  learning something  new that  you always
wanted (i.e.,  maybe you  are new to  programming or
your work didn't give much leeway, and so on).

This does  not  necessarily  mean a  coding
skills though:

+ Have you ever wondered how blind coders work?

+ What  if you  could try  out an  (language-agnostic)
  architecture you were always interested in?

+ How to design and collaborate on (large) software projects?

+ (Anything else to add?)

An important part of  learning is failure, and there
should be  a safe place  to do so  without judgement
and negative  consequences so that we  can all learn
from it.

At  the risk  of  belaboring the  point,  a goal  is
therefore to help gain experince in the field and to
successfully apply for tech jobs for all involved.

### 3.2 "Specifics"

For  example,  there  are many  frameworks,  but  no
application (either back- or  front-end) has to be a
monolithic beast either. The  front-end can be built
from modules via
[Web Components](https://en.wikipedia.org/wiki/Web_Components),
using  React,  Angular,  Vue,  etc.  (just  to  name
to  the  most  popular  ones), but  one  could  also
opt  to use  Elm,  PureScript,  Ur, Elixir,  vanilla
JavaScript/CSS/HTML, and so on.

The same goes for  the back-ends: Haskell and Prolog
are fundemantally  different from  JavaScript, Ruby,
Python, Java,  C, but  how would  you know  what you
like without giving them a shot?
