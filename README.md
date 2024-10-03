# stremio-infuse-external-player

Use with Stremio Web 5.0 on macOS

Select External Player as MPV

The Apple Script use for this:
        --on open location schemeUrl
	set a to "https:"
	set oldDelims to AppleScript's text item delimiters
	-- This saves Applescript's old text item delimiters to the variable oldDelims.
	set newDelims to {"mpv://https"}
	-- This sets the variable newDelims to our new custom url handler prefix and the prefix for the page number argument.
	set AppleScript's text item delimiters to newDelims
	-- This sets Applescript's text item delimiters to the newDelims.
	set param to item 2 of the text items of schemeUrl
	set pa to a & param
	
	--display alert "done " & pa
	do shell script "open -g 'infuse://x-callback-url/play?url='" & pa
	-- This display the result
        end open location

