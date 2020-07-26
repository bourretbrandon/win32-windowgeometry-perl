# win32-windowgeometry-perl
Perl 5 module to search for open windows by title and move/resize them

Brandon Bourret (phatwares@cpan.org)

SYNOPSIS

use Win32::WindowGeometry;
  
my @all_windows = ListWindows('');

foreach(@all_windows)

{

    if($_ =~ m/firefox/i)
    
    {
    
        AdjustWindow($_, 0, 0, 1024, 768);
        
    }
    
}
 
my @specific_windows = ListWindows('chrome');

foreach(@specific_windows)

{

    AdjustWindow($_, 50, 0, 800, 600);
    
}
 
my $super_specific_window = ListWindows('zoom - meeting');

if(length($super_specific_window))

{

    AdjustWindow($super_specific_window, 0, 0, 1920, 1080);
    
}

Pollutes the namespace with two functions: ListWindows & AdjustWindow.

METHODS

ListWindows

ListWindows('');

Returns a list of all open windows.

ListWindows('search_string'); # case insensitive

Returns a list of open windows whose titles match (or partially match) the provided 'search_string' argument.

AdjustWindow

AdjustWindow('full_window_title_string', int_X_Position, int_Y_Position, int_X_Dimension, int_Y_Dimension);

Sets a window (provided by the full name of the window's title) to an x,y position with an x,y dimension.

Notes

I just whipped this up out of necessity when I had a project where I needed to automate arranging/resizing some windows. I tried using an app called "cmdow", but it hasn't been updated in years, and it made my anti-virus go crazy. So it seemed best to make my own solution.

There is plenty of information around the web on how to 'FindWindow', 'GetWindow', etc. But not so much about moving/resizing windows. It seemed like a good idea to put this out for the community.

Warning

This has not been rigorously tested, and there's not a great deal of error checking or data validation going on under the hood. You may want to add some of your own checks/validations for safety/functionality.

Version History

1.01 - Initial Release

1.02 - Fixed this POD document

1.03 - More documentation fixes

Permission is granted to use this software under the same terms as Perl itself.

Refer to the Perl Artistic license for details.
