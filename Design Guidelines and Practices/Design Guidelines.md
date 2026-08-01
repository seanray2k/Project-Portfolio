# Design Guidelines
The following guidelines were developed over years of working with the OnShape cloud-based CAD software with embedded versioning and release histories. Different high-level projects have warranted revised organization and design strategies depending on constraints and desires, or different software's lacking the same hierarchical organization, however the same guidelines are still applicable to some extent.
## Design Order of Operations
1. A design idea/request has been presented to the team.
2. A design idea/request is assigned by the team, typically at an iteration meeting.
3. Initial ideation is done. This includes basic research of other similar concepts, design sketches, extremely rough/generic CAD, simulations, etc.
   - All work done at this stage should be very simple and conceptual in nature. The point is to express initial ideas in a simple and understandable way. Precise CAD or modelling is not needed at this stage, especially because a lot of it could change post-kick-off. You should not be spending a ton of time at this stage (maybe a week or two at most).
   - Any CAD should be done in the relevant Sandbox folder.
4. A kick-off meeting is had. The link to the Kick-off meeting template can be found here. Please make a copy of these slides and move it to this folder for Humanoids projects and this folder for Exoskeleton projects. All teams should be present to express their opinions, needs, and concerns.
   - Make sure to answer all of the questions and presentation points this template asks.
   - Make sure to leave room for discussion. The point of a kick-off is to get ideas and desires from the rest of the team early in the design process.
   - The end of a kick-off will decide if a design thrust is a new project or just a revision of an older project.
6. For a new project, start a new project document in OnShape. A template for the project document is located in each robot’s Project Documents subfolder using the 000 designation. Make a copy of this document and change what is needed to be changed. Also make a new progress presentation (here for Humanoids, here for Exoskeletons). Copy the Template Slides document (000 designation), fill out the first slides, and then add to it as the design progresses.
   - For a revision, make a branch in the old project that this revision is based on. Name the branch appropriately (“Develop - DESC” is a good structure to use). For your progress presentation note-keeping, use the slide deck from the project this revision is based on (eg. if it’s a revision of the AX030 project, add to the AX030 slides). Previous slide decks are located here for Humaniods and here for Exoskeletons.
7. Create! Work in CAD, start exploring hardware needs, loading situations, aesthetics, etc. This is your time to make the fleshed-out design that fits the group’s needs as closely as is realistically possible.
   - It is beneficial to periodically have check-ins with the rest of the hardware team through design reviews, discussions at iterations or stand-ups, or desk-side chats.
   - Constantly update your progress in your progress presentation Slides document. Note down important decisions, design methodology, relevant links, etc. Anyone reviewing this slide deck should be able to understand all of the major decisions that happened throughout your design process.
   - You may copy and move any relevant document tabs from the Sandbox into the relevant document if desired.
8. When your work is near completion, have a large-scale design review. Hardware team should be present, and other teams should be encouraged (but not required) to come. Present the minutia of your design and all of the work you put into making it happen. Present nicely-made assemblies and subassemblies if relevant.
   - Design review slides should be kept inside the relevant project’s Progress Presentation slide deck.
9. Once the design is reviewed and edits are made, make necessary drawings and start gearing towards manufacture. Clean up assemblies and subassemblies in your document and make sure everything looks good.
10. Merge relevant branches and make an OnShape Release. Update assemblies to reference the Release in Main.
11. Submit quotes and start the purchasing process!
12. Once manufactured parts are received, assemble everything to make sure fit and function are good. If a revision is needed, repeat this entire process. If it’s good to go, work out a good time with the team to get it on the robot.
13. Update your edits in the relevant high-level documents. This step might happen before the previous, have a conversation with the Controls/Software team to discuss when they would like the model ready to use.
14. Your project is now complete!

## OnShape Organization
### Folders and Organization
- In a robot’s subfolder, there will be four folders.

   1. ?? High-Level Assemblies: Houses all of the high-level documents that reflect the current state of the built robots IHMC has track of.
   2. ?? Project Documents: Houses all of the current and future design work of the given robot. There should be no subfolders inside of this folder.
   3. ?? Sandbox: Houses all of the early project experimental spaces to get design concepts to a good enough spot to have a kick-off about the project. These documents can be moved to the Project Documents folder and renamed after kick-off if desired.
   4. ?? Old Naming Structure: Houses old design work that may or may not be referenced in current designs, but which does not follow current organization and naming conventions.

- ?? delineates the robot’s two-letter shorthand designator. For example, for Alexander, it would be AX. For Link, it would be LK.

### High Level Documents
- There is a high-level document for each iteration of the robot that exists in “real life”. That is to say, if the robot is made and assembled, there is a living OnShape document that reflects the real-life robot.
- These documents should be named in such a way that easily identifies it to the real-life robot it represents.
- If a subassembly is being redesigned/replaced on the robot, the high-level document for that specific robot should be branched, and edits should be made in that branch. The branch can only be merged back to Main when the subassembly is assembled and physically on the robot.
   - Only merge back to main when the subassembly being redesigned has been released, and make sure that is the referenced version before doing the merge.
- DO NOT make any versions in the high-level documents (not even in a branch). Only releases should be made after a branch and merge is done.

### Document Naming
- Documents of ongoing or future projects should live in the “?? Project Documents” folder.
- Documents should contain the following folders in this order:
   - Subassemblies
   - Part Studios
   - Drawings
   - Hardware
   - CAD Imports
      - This folder will be made automatically when you import a part. Don’t try to make it yourself. If you don’t import any parts, you will not have this folder.
- Documents should follow this naming structure:

Slide1.PNG
### Assembly Naming
- Assemblies should live in their relevant document.
- Assemblies should follow this naming structure:

Slide2.PNG
- Mirrored assemblies and subassemblies will have related numbers. Right-side assemblies should be 01-50, and left-side assemblies should be 51-99.
   - Assemblies that are mirrors of each other should be incremented by 50 from one another. For example, if “right knee” is A03, then “left knee” should be A53.
- Subassemblies should be in the folder labelled “Subassemblies”.
- The top level assembly that would be brought into the high-level robot document should be kept in the main tab space as the very first tab of the document. This assembly should be A01 (and A51 for the mirror side).

### Part Studio Naming
- Part Studios should live in their relevant document.
- Part Studios should follow this naming structure:

Slide3.PNG
- Mirrored parts should be made inside the initial part studio. A separate part studio should not be made just to mirror a part.
   - If there is an extenuating circumstance that requires a new part studio for a mirrored part, the mirrored part studio should be incremented by 50 from the other. For example, if “right knee” is P03, then “left knee” should be P53.
- Part Studios should be in the folder labelled “Part Studios”.

### Part Numbering
Parts should follow this naming structure:

Slide4.PNG
- Notes to the above when using OnShape:
   - A part’s “name” is the same as the above, but without the revision letter and with a descriptor added (eg. AX031-P06-08 Foot Cover).
   - When putting a part number into OnShape through the part’s Properties, leave the revision letter off of the “Part number” field and instead put it in the “Revision” field. When making a drawing, the template for adding the part number engraving will re-combine them.
- Mirrored parts will have related numbers. Right-side parts should be 01-50, and left-side parts should be 51-99.
   - Parts that are mirrors of each other should be incremented by 50 from one another. For example, if “right cover” is 03, then “left cover” should be 53.
- All parts should start at revision A and increment alphabetically from there. A revision letter is only assigned once the part is being sent for manufacture. There is no need to assign revision letters before then.
- If a part is pulled from another document with a different name, that name should be maintained unless any edits were made to that part, in which case it should be given a new number.
   - It is also preferable to remake parts and note the name/part number of the original part it was created from in the part properties (in the Description). Continuously deriving parts from older projects and editing them will only bog down load times and create broken relations later on.
- If a part studio has parts that are for reference (such as COTS parts or parts derived from other places for reference), make sure to delete them or name them in such a way that makes it clear this is not a part manufactured from this part studio (such as adding REF to the beginning of parts just for reference, or DER to the beginning of parts that will be derived into other part studios to finish modelling).

### COTS Part Numbering
- For COTS parts, use the “Standard Content” in OnShape’s part insert feature whenever possible.
- If you need to add a part that isn’t in the Standard Content, import the part to the document in a Hardware folder. Refer to the section of this guide starting at Slide 12 and going through Slide 34 to name the part properly.
- Make sure to defeature parts where possible. This helps with document load times and rendering.

### Releases and Versioning
- Do not release a document with broken relations/mates. Make sure your document is clean and functional before releasing it and integrating it into the high-level documents.
   - It is recommended to branch the high level document and update your subassembly before doing the release. Some assemblies behave well in their own subassembly, but break the instant you insert them into another document. Update to your new assembly into the high-level branch, use the configurations to “move around” the segment and adjacent segments, make sure everything is solid.
   - Try to limit features in assemblies that are not fully constrained. Unconstrained motion rarely leads to good things in the full assembly and often leads to problems down the road.
- When doing a revision to a subassembly that is not considered a project, make sure to make a Develop branch off of Main to do your work in. These workspaces can later be pruned (deleted) after they have been merged back to Main.
- Releases should only be made in Main. A Release done in a branch could get lost over time, it’s better to keep it consistently in Main for easy reference.
- When development is done in a branch, the branch should be merged to Main and a release should be made referencing only the parts that changed. Parts that were not edited in any way should not be moved to the next revision value. The relevant assemblies should then be updated in the Main workspace to reference the new revision parts.
- After a document has been Released for the first time, all assemblies should be updated in Main  so that the parts native to that document refer to that Release. Assemblies of subsequent Releases should be updated to refer to new revisions of parts. Parts that were not changed between Releases should refer to the earlier Release.
   - For example:
      - I have a document of Release A. After making the Release A, I need to go into the assemblies/subassemblies and update each part (right click part in feature tree > “update linked document” > change to release version).
      - The document needs a revision, so I make a branch. I make changes to Part 2 and Part 4, but not to Part 1 and Part 3. Thus, Part 1 and Part 3 do not need a revision and should not be included in the Release B.
         - While working in my branch, I go into the assemblies/subassemblies and change Part 2 and Part 4 to pull from the current workspace (right click part(s) in feature tree > “update linked document” > change to current branch workspace). Here I can check that everything still lines up between the revisions.
      - After making Release B, I need to go into the assemblies/subassemblies in Main and update Part 2 and Part 4 to be from Release B. Thus, Part 1 and Part 3 will still be referencing Release A, and Part 2 and Part 4 will now be referencing Release B.
- BOMs can be pulled from the most recent Release. Drawings will need to be pulled from their relevant revision’s Release.

### Housekeeping
- Use “actuator bricks” instead of fully featured actuators in your main assemblies. The internal dynamics of the actuator are rarely if ever important to the overall robot dynamics. All it does is bog down load and render times.
   - Using bricks means that, in some configurations, bolts and pins mounting the actuator may “interfere” with the actuator. This is fine. Just make sure the interference makes sense.
   - Confirm that the brick you are inserting is a part, not a surface. Make sure it has the proper weight associated with it.
- All assemblies should include a “Suppress Fasteners?” and “Suppress Electronics?” configuration. This is important for rendering and URDF exporting, as these features create a lot of unnecessary bulk in those files.
   - Because of this, fasteners and electronics should rarely (if ever) be mated in such a way that suppressing them breaks/unconstrains the assembly. Mate parts in such a way that relates the parts outside of these parts.
      - If it cannot be avoided, do not include that part in the suppress feature.
- Confirm joint limits in the high-level assembly before releasing it. Make sure what your subassembly uses is the same as what’s in the high-level.
- Part colors in part Appearance:
   - Hex codes:
      - Black plastics: #4D4D4D
      - Blue plastics: #2B8EC7
      - Carbon fiber: #4D4D4D
      - Black anodized metals: #4D4D4D
      - Blue anodized metals: #2B8EC7
      - As machined metals: #A5A5A5
      - Fasteners: #A5A5A5
      - PCBs: #008000
   - All others, get as close to the real color as you can.
   - Every part should have an assigned color. Nothing in a release should have the “default” random colors OnShape assigned at part creation. Even if the part is completely obscured, it should be properly colored in case it is ever unhidden for pictures/screenshots.
- Update and make sure of the Progress Presentation for your relevant project. Good note-keeping of design decisions prevents confusion down the road, when someone inevitably picks up your project and attempts to understand why certain things were done certain ways. Good documentation minimizes the amount of time someone will spend making a mistake you may have already made yourself.
   - Keep all design reviews (even major ones) inside of this same slide deck. Keeping it all in one place makes it easy to reference down the line.

### Tips
- Check the “interference detection” on assemblies before releasing them. It’s a small check that many of us forget, and doing it would save a lot of heartache later.
- Double-check that every part (even electronics and fasteners) have an associated material/mass before releasing the document. Checking the mass of the entire subassembly will give you an error if something is missing a weight.

## Organization Methodology
### Delineating a New Project
- A new project document should be made for “major development pushes”. This will usually (but not always) include design pushes that require a kick-off meeting.
   - A kick-off meeting implies the necessity of group input early on in the design process, which isn’t needed for minor revisions to parts.
   - The end of the kick-off meeting should be used to discuss with the hardware team if the current design push necessitates a new document and project designation, or if it’s only a branch revision.
      - This decision may change as the project progresses.
   - All work prior to a kick-off should be done in a sandbox. Designs should not be very realized prior to kick-off, as a kick-off could dramatically change a project’s direction. Project documents or branches should only be made after a kick-off.
- If a development thread is minor enough, it should be done as a branch in the original relevant document instead of as a new project.
- A project’s number is an arbitrary number and does not delineate a specific segment or area of the robot. Numbers should be assigned sequentially based on the last-used project number.
   - For example, AX021 could be “Head V2”, AX022 could be “Thigh V4”, and AX023 could be “Head V3”.

### Projects Instead of Versioning
- Versioning the robot itself made no sense due to the fact that we were maintaining two different versions/copies of the robot in real life and that subassemblies would be redesigned and versioned at different times and different frequencies, making delineating the “next robot version” difficult.
- Maintaining and versioning a single document for each subassembly was considered, but there were times when making a new document would make more sense than just versioning and deleting 90% of the content. The eventual lengthy document history would also be daunting, and referencing parts from differing versions would be tricky.
- We considered some combination of versioning and new documents, but version tracking between the two became difficult, and a naming would be come tricky.
- We decided that the best and most sensical path forward would be to treat every new “major development” as a “project” that got its own dedicated document and would track sequentially through the numbering.
   - This allows for implied version tracking and also makes room for parallel development on similar parts of the robot.
   - This also allows us to make projects that don’t necessarily need to be a main part of the design pipeline. A project could be designed and explored, but never manufactured.
      - To be clear, this is different from a sandbox, which is a more experimental space and doesn’t have any major development behind it.
