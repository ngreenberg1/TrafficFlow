
### 10/24/24
# **Analysis**

#### The code appears to be broken up into 3 sections:
    1. Variable declarations (Lines 1 - 35) -Stands alone and does not call any methods.

    2. Setup procedures (Lines 38 - 161) - 
       The parent method is to setup and is linked to the setup button on the GUI.
       This method calls various other methods in the setup procedures section as well as a few methods from the runtime procedures section.

    3. Runtime procedures (Lines 164 - 356)  - 
       The parent method is to go and is linked to the go button on the GUI. 
       This method is the only method in the entire program to iterate the global time variable tick. 
       As such, any runtime behavior will need to be called from this method.

<p>This is a very basic language and seems to rely almost exclusively on chained method calls. Since there is no way to make a class or separate code into separate files, it will likely be very difficult to add any desired modifications to the code within the existing method structure as any changes will propagate down the call chain.

EG…If we modify method X, then that change at X will affect all subsequent methods.

As such, modifications should be done by adding additional methods and calling them at either setup or runtime from the GUI. Support for this style of modification can be seen during the setup method…
<p>

    1. On line 50 - setup-patches is called

    2. On line 95 (the setup-patches method) - 
       EVERY patch is asked to set its initial variables in the following manner:
        a. Not an intersection
        b. Auto? = false
        c. Set color to brown
        d. If we were to stop now, every patch on the GUI would not be an intersection, 
            would have its auto? Boolean as false and would be brown. Continuing however…

    3. The initialized patches, now all uniform, are now further 
       separated into road and intersection patches on lines 109-116 by 
       overwriting their attributes with the subsequent roads and intersections logic.

<p>This means the methodology for assigning variables, behaviors, characteristics ETC, is an additive process EG… Setup all patches as patch type 1, then, from the set of patch type 1, assign a subset as patch type 2 -> repeat until done. Through the setup process, at some point in it’s “lifecycle” each patch was of the most basic type, AKA the first patch type it was initialized as, in this case, the brown patches.

This is in contrast to how I think we would have instinctually accomplished this goal…Define different sets of logic that set ONLY the patches that we want as this patch type, instead of all assigning all of the patches as patch type 1 and then re-assigning those we want to be of a different type.
</p>
