leaena.github.io
================

###I can has static blog! (migrating from wordpress to hexo)

So in order to be a One True Geek&trade; I decided it was high time I switched over to a staticly generated blog. So this all is COMPLETELY FREE (except the domain name, much love to [namecheap](http://namecheap.com)).

####Step 1 (you cut a hole in a box):

Export all the things!!! Seriously, back up all your shit. I already use [disqus](http://disqus.com/) for comments and [cloudinary](http://cloudinary.com/) for most of my image hosting (lemme tell you, it was a bitch to go back and find which pictures I'd imported before cloudinary, but c'est la vie). All I had to do was use Wordpress' handy dandy export link. Most other blog providers have them too, they ususally (read **should**) export as XML. (_note:_ After this initial cloudinary import I will probably store my images in my github directory, because fuck it)

####Step 2:

Decide what the hell static site generator to use. There are [a lot of them](http://www.staticgen.com/). My personal preferences were:
1. Something in a language I understand well (preferably JavaScript or Python)
2. Something that has a handful of support/plugins/etc or that I can easily hack apart.
3. Easy deploy to github pages and other things (in case I decide to rethink my GitHub move).

And the winner was: [Hexo](http://hexo.io/). Node.js, my favorite thing ever? Check. Good support/user experience writeups? Check. Quick deploy from the commandline? Checkity check check.

####Step 3:

Import that shit. Remember all the stuff we exported? Now we get to reimport it. I like to do this before I decide on my theme/layout so I can have a feel of what the actual blog looks like. Hexo has an [auto importer](https://github.com/hexojs/hexo-migrator-wordpress), lots of them do.

_another side note:_ The auto importer **will** fuck up on a few of your posts. Be calm. Do a quick runthrough and make sure things look vaguely OK. Fix what doesn't. Zen, no?

####Step 4:

Makin' magic. Buff that shit up, make it pretty, make it ugly, make it yours. Find a theme, a good organization strategy, whatever. This one is up to you. I took a base them and fucked with it until it looked gorgeous to me.

####Step 5:

More magic (this time the black magic variety). If you want a domain name attached to all this (I do), it's time to take a deep breath and follow some tutorials on CNAME/ALIAS setup for GitHub pages EXACTLY. You will probably screw it up (I did), just keep rereading and as we have all learned in programming try to justify makes you think the thing that you just did will do the thing that you think it will do. Yikes. Good luck.

####Step 5b:
I wanted to keep email stuffs. So I also had to convert my MX/mail DNS stuff somewhere. I chose [Zoho Mail](http://www.zoho.com/mail/) because there aren't many free options. Jury is still out.

##That's it! Hopefully...

###If you have ANY questions about doing something similar to what I've done. Please feel free to email me: lindsey @ clevergirl.me (fingers crossed that the MX/mail DNS worked properly, amiright?).  I might not be able to help, but I will try my best.
