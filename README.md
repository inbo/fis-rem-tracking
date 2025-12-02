# fis-rem-tracking
A public repository for the animal tracking for REM by INBO Grofwild

NEW REPO FOR ANIMAL TRACKING BY OTHERS

Hello! You've entered the wonderful world of animal tracking for REM. This methodology can be a lot at first, but I've set up this repo to make your life slightly easier. Please *CAREFULLY* read this before starting.

-------------------------------------------------

Animal tracking happens within the scope of the Random Encounter Model (Rowcliffe et al. 2008). With this model, densities can de estimated for animal species without unique markings. The whole workflow for this model has been integrated in Agouti. Here are the different steps. More detail on each step can be found further down in this document.

1. Fieldwork for *camera calibration*. With our trusty *stick with black bands*, we position ourselves in the camera field and make sure we have enough unique stick positions on photograph.
2. Uploading the photos. The usual.
3. *Camera calibration in Agouti*. This constitutes of tagging each unique stick position with a "bottom" and a "top". Use the groups of black bands to help you identify the different Heights.
4. Annotation. The usual.
5. *Tracking of animals*. This is where this repo comes in. You will follow the chosen study species in their different sequences and this will give us the necessary information regarding speed and detection angle and radius.
6. Analysis. The usual.

-------------------------------------------------

MORE INFORMATION ON CAMERA CALIBRATION IN AGOUTI

When the pictures of the field calibration have been uploaded in Agouti, we then need to translate the information from photograph to pixels. To do this, annotate the calibration sequence(s) with "Deployment calibration" in Agouti. For each unique stick position in the sequence, you can then click on the top of a group of black bands, first one that acts as "top of stick" -- in the pane on the right, mark the associated height in m. Then click on the top of another group of black bands for "bottom of stick" and write down the associated height.

Groups of black bands and their Heights:
1 -- 20 cm off the groun
2 -- 40 cm off the ground
3 -- 60 cm off the ground
4 -- 80 cm off the ground
5 -- 100 cm off the ground
Tip: where the stick touches the ground, that is height 0 cm :-)

Caution: the bottom of the stick needs to be ON THE GROUND and the stick needs to be STRAIGHT in the field of vision (or as much as possible).
Further caution: you might not always see all the groups of black bands (vegetation, terrain, etc.). No worries, just choose two combinations for "top" and "bottom" that are clearly visible.

To make things easier in Agouti, we have the following rule:
Annotaters will annotate the relevant deployments as "Deployment calibration" but they will NOT actually calibrate -- this is best done by the person also tracking. To easily find the relevant deployments when you actually start calibrating, go to Observations and filter on Observation type == "DeploymentCalibration" (maybe adjust the time frame in which you're filtering). Once you've actually calibrated, finish up by clicking on "Validated". This will show up in Observations and you will then immediately see which ones you've already done.

-------------------------------------------------
 
MORE INFORMATION ON ANIMAL TRACKING IN AGOUTI

Once annotations for your study period have started (or even ended, depends on how many exports you want to wait for while working), you can start tracking. For this, you will exclusively work in your assigned study area folder in this repo.

Start by opening your relevant script for animal tracking. Last I tested, it should work without any issues, but regular updates of R and associated packages might cause warnings or errors. If this happens, don't panic and ask Sander for help :-)

The script first gets the relevant export from our team's Google Drive and extracts the necessary data. Then it filters out the relevant deployments, more specifically deployments within the right study period and with actual calibration in the field (it has happended that we forgot a camera in the past -- we're only human!). With this deployment list, we start filtering out the relevant species (no need to see species that you will not track right now -- trust me, this will save you a lot of time!).

Finally, it will filter out all the sequences that already have been tracked. This means you'll never see a sequence twice. When it first opens, you will decide if it is trackable (will explain in a bit) -- if yes, the sequence will be saved as "tracked" -- if not, the script will save the sequenceID as "done", meaning that it was looked at but deemed untrackable. This means nobody will ever look at this sequence for tracking ever again, so don't dismiss sequences too quickly! But this system ensures you will not get to see the same sequences over and over again. All the "sequences alread done" over the last few years are saved in your respective "tracking_seq_done.csv" in your Input folder.

Finally, for the tracking itself, we use a for-loop. This will go through the list of sequences that still have to be tracked and open them in Agouti one by one.

To track:
1. Select the right observation and click the pencil to Edit.
2. Within the observation, choose the first foot on the ground you see of the first animal you see. Go through he pictures and, every time this same foot touches the ground somewhere else in the picture, click the foot.
3. Once you've gone through all the photos of the sequence, you should see your animal's track on the screen.
4. Save the observation.
5. Close the Agouti tab in your browser.

Now we get to the little popup that is part of the for-loop. This ensures your computer doens't get flooded by all the relevant sequences all at once. Once you've finished tracking a sequences and closed the Agouti tab in your browser (see point 5 above), you can do the following:

1. Click "Yes" -- the for-loop will continue and show you the next sequence.
2. Click "No" -- the for-loop will break and no longer show you sequences.

The second option allows you to stop tracking at any point in time (end of work day, fried brain, short or long interruption -- whatever reason).

While you are in the for-loop, each sequence you open in Agouti will have its ID saved in your respective "tracking_seq_done.csv". At the end of your tracking session, check in GitHub Desktop that everything has been saved and commit these changes. This way, the next time you start tracking again, the sequences you just did will no longer be shown to you. Trust me, this is the way to stay sane.

*IF YOU GET TO THE END OF THE FOR-LOOP*
Congratulations, you've tracked everything... from this export! Make sure to ask for a new export in Agouti (ask Jim he should have all the necessary rights) and that this one gets uploaded in the Google Drive folder (ask Sander, he knows what and where). Make sure the name of the exported zip-file is the same as what is already in the Google Drive so you can simply replace the existing file and the gfileID stays the same -- that way, no need to make changes in your Input code.

(Also, from experience: if something seems off with the data because you know you should be seeing some specific changes but you're not -- check the date of the latest export, check that there is only one export in the Google Drive folder and check that the gfileID hasn't changed (ask Sander). More often than not, somebody didn't "replace existing file" and now your export has a new gfileID. Luckily, this can easily be fixed an you will be one your way again tracking in no time.)

The for-loop is only every 100% done when everything from your study period has been annotated and tracked. And if that is done, there is always next year :-P But we won't do that to you, you will have survived enough with one year of tracking.

-------------------------------------------------

Yours truly,
Lynn Pallemaerts
10th of November 2025

-------------------------------------------------

QUESTIONS AND WHERE TO GO

Questions about R and GitHub ? Ask Sander
Questions about the model ? Ask Jim
Questions about the workflow ? Ask Lynn. If unavailable, ask Sander he'll have it figured out in no time

-------------------------------------------------

FURTHER READING

Rowcliffe et al. 2008 (https://besjournals.onlinelibrary.wiley.com/doi/10.1111/j.1365-2664.2008.01473.x)
ENETwild Consortium 2024 (http://efsa.europa.eu/en/supporting/pub/en-9084)

Theses from previous students who worked with this model can be found in the Documentation folder of this repo.
