

* meeting temp
    * remove services, keep UI
        * no maintenance for a while, sounds like a liability if no use
        * why do we even want UI ?
    * memberships / c&e are integrated, coupled?
* monday org	 
    * gather loyalty/membership/events&classes materials
    * plan who we will reach out to    
        * figure out memberships / events&classes, learn from monday meeting guys
* stuff
    * leonard and eric's game: [https://leonardmeagher2.itch.io/kingdom](https://leonardmeagher2.itch.io/kingdom) 

------- meeting notes (loyalty 2.0 team meet)



* GIH: ping eric for names and reach out to them for meet
* IMPORTANT: prep doc for edmund re classes & events
* people
    * marc chaix
        * product manager
    * apoorv bansal
        * product manager
    * michael chen
        * was FE eng on memes team
        * also worked on membership
    * patrick lam
        * worked on memes, currently PCM team
        * services dev
    * dan pickering
        * fe eng on memes
    * mark zehr
        * backend eng, worked on "events and classes"
    * ivan
        * fe eng membership and memes

-------  OLD (BELOW)



* goals
* learn
    * launch darkly (feature flagging)
    * adobe audience manager / adobe target
    * sonarqube
* notes
* 
    * eng
        * wae-partials
            * uses Lapel for ab testing, which is why we care. this is our package.
            * lenny hates this package, has too many consumers that can break if we change something, would prefer to touch it as little as possible
                * also turn off ab tests when not using, sometimes we forget and then its keeping experimental dangerous code longterm
            * serves header and footer for jsp and for nextjs
            * gives you some html
            * lululemon/wae-partials
            * cool thing: has a prerelease thing "yarn release --any-branch"
                * releases npm package with dynamic name to test releaesDS*
            * to actually release you have to manually increment version
        * peps-remote-components