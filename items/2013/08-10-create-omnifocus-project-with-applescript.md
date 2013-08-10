---
published: 2013-08-10T17:25:06+02:00
title: Create OmniFocus Project with AppleScript
---

At work one of my duty is to take care of purchase orders for my team mates. The workflow involve always the same three steps.

Being an Omnifocus user, I wrote a small AppleScript that create those steps for me.

~~~~~~~~~~~~~~~~~~~~~~~~~~
-- Entry point when run

on run
    display dialog "Enter purchase order description:" default answer "Purchase"
    createOmniFocusTask(the result's text returned)
end run

-- Create tasks in Omnifocus

on createOmniFocusTask(eventName)
    tell application "OmniFocus"
        tell default document
            -- Grab the context
            set purchaseContext to first context whose name is "Emarsys"

            -- Create the task inside a project
            set fld to first folder whose name is "Emarsys"
            tell fld
                set proj to first project whose name is "Single Actions"
                tell proj
                    -- Create parent task and its subtasks.
                    set parentTask to make new task with properties {name:eventName, sequential:true}
                    tell parentTask
                        make new task with properties {name:"Print Formular for " & eventName, context:purchaseContext}
                        make new task with properties {name:"Get the Sign for " & eventName, context:purchaseContext}
                        make new task with properties {name:"Order for " & eventName, context:purchaseContext}
                    end tell
                end tell
            end tell
        end tell
    end tell
end createOmniFocusTask
~~~~~~~~~~~~~~~~~~~~~~~~~~


Copy and paste that into a new script in AppleScript Editor (or download a copy [here](https://github.com/basetta/dotfiles/blob/master/applescripts/e3purchase_omnifocus.applescript)) and try it out.

Of course, you have to adapt a little bit if you do not have an Emarsys context.