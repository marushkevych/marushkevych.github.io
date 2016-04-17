---
layout: post
title:  Jekyll has stupid permalink date bug
subtitle:  but they think its a feature?!
date:   2016-04-17
categories: jekyll 
---

Jekyll generates permanent links to your posts using date provided in post metadata.
So if your metadata headaer looks like this

```
---
layout: post
date:   2015-07-24 1:30:00
---
```

Then you would expect that Jekyll generates the following blog URL:

```
/2015/07/24/blog-name
```

But, turns out, it doesn't always generate this URL!!! Sometimes, if you lucky it will, but sometimes it will look like this:

```
/2015/07/23/blog-name
```

What? Its a permalink! Its not supposed to change!!!

Yes, if your local time is not UTC, Jekyll will convert specified time to local time and use that date to generate blog URL. And the most frustrating thing is that they know about it and still in version 3 its not fixed because they think its not  bug! WTF?!

Anyway... The workaround it to not use time portion of the date metadata: 

```
date:   2015-07-24
```

Or tell Jekyll that your local time is UTC in your  `config.yml`:

```yml
# this is needed to fix stupid bug - jekyll generated post url from post metadata using local timezone. So if you provide time portion of the date, you might get link generated day later or earlier!
timezone: UTC
```
