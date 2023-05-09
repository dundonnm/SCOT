update 12/7/22 7:40 - nmd
- now loads in from .acq files
- now uses a gui to allow user select contractility channel
- now uses a gui to allow user select respiration channel
- cell 2 now plots 10 s of data to let user specify amp threshold in findpeaks
- minor tweaks to x and y zoom on interactive plots

update 12/8/22 10:30 - nmd
- minor tweaks here and there - considering using dZ for temp, then those temp indices for cont amps

update 2/9/22 6:48 - nmd
- beta version should be good to go
- using acceleration channel to identify heartbeats (equivalent R intervals)
- Cell 1 loads the data via a GUI
- user specifies which is acceleration channel and which is respiration channel
- user specfiies if respiration channel needs lowpass (if using z0)
- give this a minute to load/preprocess everything, "data loaded!" will appear in progress bar
- first plot (Cell 2) plots a section (20 seconds worth) of acceleration peaks to pick a threshold for min amplitude. Enter in the accompanying GUI.
- second plot (Cell 3) interactive plot of entire series of acceleration peaks to adjust errors in peak identification (see instructions in cell)
- third plot (Cell 4) replots contractility and allows a final adjustment
- Cell 5 models out respiration (volume and phase) and saves a csv. A column of peak times and contractility.

- adding tutorial.md
- deleting various old files

update 2/10/22 -nmd
- change to miniMEAPsys.py, can now work with a respiration belt, if specified
- change to miniMEAPsys.py, user now specifies an output filename, prepopulated with default

update 2/13/22 - nmd
- adding new function for cell 4, adjust_peak_amp, that only changes peak amplitude
- adding new function for cell 4, meap_dat_cell4, that only changes peak amplitude
- Cell 3: plot now updates number of peaks as they are added and removed
- loadem now does a plt.closeall and a 
- bug fix - find_preceed_peak - now searches either in the preceeding 250 datapoints for cont peak, or if peak ind <250, the entire series up to that point
- bug fix - meap_dat - now boolean test to make sure there are two peaks either side of meap_dat loc
- bug fix - duplicate shift_peaks removed

update 3/17/23-nmd
- notebook and sys file name changes, name changes in example dataset, updated tutorial

update 5/8/23-nmd
Cell 2: comptue_peaks - peak_times, peak_vals and peak_inds all now outputted as part of cont_dict
Cells 3 and 4: peak_times, peak_vals and peak_inds all now operate through the cont_dict dictionary, also updates to remove_point, add_point and meap_dat, adjust_peak_amp and meap_dat_cell3 functions
adding pickle_save funtion. Cell 5 now exports a pickled cont_dict in addition to a csv, to allow a project to be reopened later
adding Cell 1A to allow people to save progress at any time
updated load_acq and loadem functions to allow import of a pickled cont_dict (.scot file)

update 5/9/23-nmd
meap_dat bugfix. indices of inserted peak_times were wrong.
Cell 3 now exclusively works with cont_dict['acc_peak_times'] and cont_dict['acc_peak_vals'] 
Cell 4 now exclusively works with cont_dict['peak_times'] and cont_dict['peak_vals'] 
This should allow user to go back and redo cell 3 if they need, after loading a .scot file completed up to cell 4 or 5

- desired future fixes: 
some kind of tkinter "kill all / close all" that can be called in Cell 1, might help with loading issues
some way of masking functions of the text in Cells 3 and 4, which make the notebook very long
Cell 1 very buggy, need to restart kernel a lot...
pickle file is massive... any way to compress? or other option than pickle?
Cells 3 and 4 probably aren't working optimally. Something not quite right with the     

if not plt.fignum_exists(1):
        canvas.mpl_disconnect(cid)
        canvas.mpl_disconnect(cidk)

I don't think this command is actually doing anything. It would be nice to have this to execute certain functions (like a save) if people close the GUIs....
