#### Qualities handling is changing

We aren't quite sure how qualities for shows have become so complicated to understand. We have several theories, but all of that is coming to an end.

First, the feature **Archive on first match** was poorly named, and caused it to be confused with and intertwined with the **Archived Episode Status** episode status over time.

**Archived Status** is only meant to be for episodes that we know we have but Medusa does not have a location for, or it does not exist at the location.

**Archive on first match** is a relic from the time when Medusa only had one quality list, back in SB days (afaik), where you needed to specify if you wanted to keep looking until the best quality in that single list was reached.

#### **Archive on first match** has been removed in develop 
With the use of two quality lists like we have for custom qualities, **Archive on first match** can be eliminated. This removes the continued confusion which caused users to mentally link **Archive on first match** and **Archived Status**, which are two totally separate features. It also greatly simplifies the code, and allows us to prepare for better quality handling and eventually user orderable quality lists ("CP Style"). It also makes it easier to add the 2k/4k/UHD qualities.

#### What does this mean for you?  
Well, if you had your qualities set up in an odd custom configuration, Medusa might think it needs to re-download something that you think it should not.

The solution is simply to change the quality settings for your shows.

#### Here is how it works
If you ONLY have qualities in the **Allowed** list (Or have a preset selected other than custom) it will stop on the first match in this list and be considered a "_best_" match, and never be replaced with a better quality.

If you have qualities in BOTH lists, it will accept any quality in the **Allowed** list, and continue looking for a better quality in the **Preferred** list, until it finds one. Once Medusa finds a match in the preferred list, it stops looking.