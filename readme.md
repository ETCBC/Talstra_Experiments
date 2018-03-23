# Participant Tracking. Files and ProceduresMade by: prof. dr. E. Talstra

Versions:
10-01-2018 [1]
18-01-2018 [2]
05-03-2018 [3]
'All code is written in Pascal'Example: Exodus 19## 1) qetps –f exodus 19exodus19.PX		        [data file: linguistic analysis from morpheme …. text level]exodus19.ct4.p		[surface tekst, presenting lines, phrases, phrase parsing]## 2) IdentifyPTC

Input:
exodus19.PX [data of analyzed text]
exodus19.ct4.p [surface text]### Task:
Output:exodus19.TXT		[surface text: lines, phrases, phrase parsing, domain numbers, domain types]exodus19.Candp		[List of PTC cand. [phrases and subphrases] + number + line + PNG + lexs]exodus19.VerbCandp 	[List of verbs as of PTC cand + code of rootf. + code of vb tense]exodus19.TP		        [List of PTC cand.: lines, dom, parsing, PNG, relation type, domain owners]exodus19.TOTPhr		[“human readable” format of file ….TP]### Problem:
This program correctly establishes almost all Candidate Participants. Some bugs left. The program does not yet find all linguistic relations between Candidate Participants. It is also missing a number of Speaker/Audience and Sender/Addressee cases in each domain. Since we do not yet know that much of the text grammar of participant tracking (the very reason for doing this project), it will take time before this first program can do much better. For that reason the next program is used: an interactive procedure of correcting/establishing relations between Candidate Participants and of correcting/establishing domain owners.## 3) CorrectPTC

Input:
exodus19.TPexodus19.TXT### Task:

[interactive procedure to correct PTCcand-relations in file exodus19.TP][to present surface text + PTCRef numbers in ….TXT ]
Output:exodus19.TPN		[corrected content of exodus19.TP]exodus19.TOTPhr2	[“human readable” format of file exodus19.TPN]exodus19.XXX		[List of PTC candidate relations (lexical and/or morph.) and domain owners]### Problem:The program does not yet present on screen all cases that might need correction;Making interactive corrections of Speaker/Sender and Audience/Addressee labels at this level of analysis is not yet possible.## 4) CalculatePTC

Input:
exodus19.TPNexodus19.XXXexodus19.TXTin a second run also: exodus19.SpAu
### Task:
The program collects all cases of each individual PTCRef Sets (at Domain level) and creates labels for each Set. A label is:  PNG + noun(s).Next the program connects Sets into Actors (at Text level) and creates labels for each Actor.PTCRefs, PTCSets and PTCActors all are listed on file exodus19.PSAListOutput:exodus19.XXXcorr	        [calc. PTCSets from PTCCand. + relations in XXX; dom. owners >> Sets]exodus19.TXTn2		[= TXT; Set numbers and Actor numbers are added to PTC candidates]exodus19.TP2		[copy of exodus19.TPN  ]exodus19.PTCList        	[Listing of text with all PTC cand, Set+Label, Actor+Label, Domain Owners]exodus19.ACTList    	[Concordance of all Actors with Sets, Domains and text lines]exodus19.PSAList        [For each PTC cand: num, Sets num, Actor num, Dom.num, Spk.num, etc]exodus19.MTR		[Presentation of text by domains, owners, actors in domain]The program is being used in an iterative way.Sets and Actors 	        [combinations of Sets] + functions Speaker, Audience .. stored or readInput/output:exodus19.SpAu 		[calc. per domain: Sets, dom. owners (Speak. Aud., etc); Sets >> Actors]### Problem:
Errors in linguistic analysis can best be observed by studying the files exodus19.PTCList and exodus19.ACTList. Corrections are to be added into file exodus19.XXX; then rerun CalculatePTC.Much of these corrections actually should be made possible by program 3: CorrectPTC## 5) RedoCalcPTC

Input:
exodus19.SpAu
exodus19.TPNexodus19.PSAList
### Task:
Output:exodus19.PSAList3	[expanded PSAList: Actor Sets added]exodus19.CSV		[PSAList3 in CSV format]exodus19.CSV2		[idem, condensed]
*lexical/semantic features info to be added by interactive procedure:*
Input/Output:        exodus19.FNames	[Actor Sets based on semantic overlap]        exodus19.FSets	        [Actor Sets based on semantic overlap + domains, domain owners]        exodus19.ANames	[Actor Sets based on referential identity]        exodus19.ASets	        [Actor Sets based on referential identity, + domains, domain owners]        exodus19.Prefs
        Results stored in:        exodus19.ActsAndSets    [inventory of Actors; identity or overlap]        (and in exodus19.PSAList3 = file exodus19.PSAList  + additional columns of lex./sem. Sets).## 6) InventoryPTC

Input:
exodus19.SpAuexodus19.TXTn2exodus19.
### Task:
Output:exodus19.PredFramesexodus19.INVDataexodus19.INVINVsort		[procedure for sorting exodus19.INVexodus19.SetsInDomexodus19.ACTinDomhebsort PredFrames 		Output: exodus19.PredFrames
sh INVsort        input:		exodus19.INV		    Output: exodus19.INV.sort        input:		exodus19.INVData	    Output: exodus19.INVData.sort## 7) InventPTCPat

Input:
exodus19.INV.sort
exodus19. PSAListExodus19.INVDList