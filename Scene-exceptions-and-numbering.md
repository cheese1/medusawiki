## What are Scene exceptions.?

Scene exceptions are alternative names that are used by the "Scene" (release groups and uploaders of shows).
Sometimes a show is called different by the indexers (eg. TheTVDB) than the torrents/nzb's files.
For example a show is called `Pawn Star$` on the indexer, but the uploaded files are named `Pawn Stars`
When this is the case Medusa cant detect the torrents/nzb's files and they will be skipped. Then a a scene exception is the solution.

To add a Scene exception go to the Show and click on the edit button. You will see a field called `scene exception`. Add the desired scene name and save the settings. 
On the next search Medusa will use the newly added scene exception name in its search and should find the show/episodes.

We have tried to automate this process as much as we could by adding scene exception lists. So for known problematic shows Medusa automatically adds those names.
However there are still shows that require manual adding the scene exception name. 
So when you have a show that requires a manual scene exception please submit a Pull Request to the respective indexer's scene exception lists ([Scene Exceptions](https://github.com/pymedusa/medusa.github.io/tree/master/static/scene_exceptions)). This also helps other users that experience this problem.

![name](https://cloud.githubusercontent.com/assets/7928052/13529717/d9ab6c86-e21d-11e5-9e01-8d53d8a7401a.png)

## What is Scene numbering?

Sometimes release groups and uploaders use different episode numbers then an indexer like TheTVDB does. When that happens Medusa can have problems downloading the correct episode.
To get around that problem there is the possibility to add Scene numbers.
This can be done manually or automatically. For manually you need to enable the `Scene` column on the show page. To do that open the show and pres the `select column` button and select the `Scene` option. Now you will see a small field in front of every episode. Here you can manually add the scene number. 
Automatic adding of scene numbers is done with the help of http://thexem.de
If you take the show `Pawn Stars` for example http://thexem.de/xem/show/1759 you see that different episode numbers are used by the indexers, but thexem.de renumbers/links them to the correct numbers so that Medusa can find the episode.
If there are problematic shows that use a different numbering scheme then please consider adding those on thexem.de so that other users can also profit from the change and don't need to manually add it locally. 

![number](https://cloud.githubusercontent.com/assets/7928052/13529718/d9ae5392-e21d-11e5-89af-435ad7706efd.png)
