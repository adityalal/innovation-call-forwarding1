# innovation-call-forwarding1









;adityaneo
exten => _22X.,1,AGI(agi://127.0.0.1:4577/call_log) 
exten => _22X.,2,Dial(SIP/2222/${EXTEN:2},,Tto) 
exten => _22X.,3,Hangup 


; dial a local 727 outbound number with area code
;exten => _9727NXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _9727NXXXXXX,2,Dial(${TRUNK}/1${EXTEN:1},,To)
;exten => _9727NXXXXXX,3,Hangup

; dial a long distance outbound number to the UK
; This 'o' Dial flag is VERY important for VICIDIAL on outbound calls, 
;exten => _901144XXXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _901144XXXXXXXXXX,2,Dial(${TRUNKX}/${EXTEN:1},55,To)
;exten => _901144XXXXXXXXXX,3,Hangup

; dial a long distance outbound number to Australia
; This 'o' Dial flag is VERY important for VICIDIAL on outbound calls, 
;exten => _901161XXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _901161XXXXXXXXX,2,Dial(${TRUNKX}/${EXTEN:1},,To)
;exten => _901161XXXXXXXXX,3,Hangup

; dial a long distance outbound number through BINFONE
; exten => _91NXXNXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91NXXNXXXXXX,2,Dial(${TRUNKIAX}/${EXTEN:1},55,To)
; exten => _91NXXNXXXXXX,3,Hangup
; dial a long distance outbound number through a SIP provider
; exten => _91NXXNXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91NXXNXXXXXX,2,Dial(sip/${EXTEN:1}@SIPtrunk,55,o)
; exten => _91NXXNXXXXXX,3,Hangup
; special extensions for North America to catch invalid phone numbers
; exten => _91XXX[0-1]XXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXX[0-1]XXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXX[0-1]XXXXXX,n,Hangup
; exten => _91[0-1]XXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91[0-1]XXXXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91[0-1]XXXXXXXXX,n,Hangup
; exten => _91XXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXX,n,Hangup
; exten => _91XXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXXX,n,Hangup
; exten => _91XXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXXXX,n,Hangup
; exten => _91XXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXXXXX,n,Hangup
; exten => _91XXXXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXXXXXXX,n,Hangup
; exten => _91XXXXXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXXXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXXXXXXXX,n,Hangup
; exten => _91XXXXXXXXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91XXXXXXXXXXXXX,n,Dial(${TRUNKloop}/8889990011112,,to)
; exten => _91XXXXXXXXXXXXX,n,Hangup
; dial a USA long distance outbound number through the loopback-no-log context
; exten => _91NXXNXXXXXX,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => _91NXXNXXXXXX,2,Dial(${TRUNKloop}/888${EXTEN:2},55,o)
; exten => _91NXXNXXXXXX,3,Hangup
;exten => 888NXXNXXXXXX,1,Goto(loopback-no-log,91${EXTEN:3},1)

exten => 8889990011112,1,Goto(loopback-no-log,9990011112,1)


; Inbound call from BINFONE
; exten => 1112223333,1,AGI(agi://127.0.0.1:4577/call_log)
; exten => 1112223333,2,Dial(sip/gs102,55,o)
; exten => 1112223333,3,Hangup

; Extension 7275551212 - Inbound local number from PRI with 10 digit delivery
;exten => 7275551212,1,Ringing
;exten => 7275551212,2,Wait(1)
;exten => 7275551212,3,AGI(agi://127.0.0.1:4577/call_log--fullCID--${EXTEN}-----${CALLERID(all)}-----${CALLERID(num)}-----${CALLERID(name)})
;exten => 7275551212,4,Answer
;exten => 7275551212,5,Dial(sip/spa2000&sip/spa2001,30,To)
;exten => 7275551212,6,Voicemail,u2000

; parameters for call_inbound.agi (7 fields separated by five dashes "-----"):
; 1. the extension of the phone to ring as defined in the asterisk.phones table
; 2. the phone number that was called, for the live_inbound/_log entry
; 3. a text description of the number that was called in
; 4-7. optional fields, they are also passed as fields in the GUI to web browser
; This is not part of VICIDIAL, it is for astGUIclient agent use only

; Extension 3429 - Inbound 800 number (1-800-555-3429) example of RBS T1
;    with 10 digit ANI and 4 digit DNIS star separated
;exten => _**3429,1,Ringing
;exten => _**3429,2,AGI(agi://127.0.0.1:4577/call_log)
;exten => _**3429,3,AGI(call_inbound.agi,spa2000-----8005553429-----Inbound 800-----x-----y-----z-----w)
;exten => _**3429,4,Answer
;exten => _**3429,5,Dial(sip/spa2000&sip/spa2001,30,to)
;exten => _**3429,6,Voicemail,u2000
; Extension 3429 - with ANI [callerID]
;exten => _*NXXNXXXXXX*3429,1,Ringing
;exten => _*NXXNXXXXXX*3429,2,AGI(agi://127.0.0.1:4577/call_log)
;exten => _*NXXNXXXXXX*3429,3,AGI(call_inbound.agi,spa2000-----8005553429-----Inbound 800-----x-----y-----z-----w)
;exten => _*NXXNXXXXXX*3429,4,Answer
;exten => _*NXXNXXXXXX*3429,5,Dial(sip/spa2000&sip/spa2001,30,to)
;exten => _*NXXNXXXXXX*3429,6,Voicemail,u2000


; parameters for agi-VDAD_ALL_inbound.agi (upto 12 fields separated by five dashes "-----"):
; Below are the parameters needed for the script to be run properly
; 1. the method of call handling for the script:
; 	- CID - 	CID received, add record with phone number
; 	- CIDLOOKUP - 	Lookup CID to find record in whole system
; 	- CIDLOOKUPRL -	Restrict lookup to one list
; 	- CIDLOOKUPRC -	Restrict lookup to one campaign's lists
;     - CLOSER -      Closer calls from VICIDIAL fronters
; 	- ANI - 	ANI received, add record with phone number (based on RBS T1s)
; 	- ANILOOKUP - 	Lookup ANI to find record in whole system
; 	- ANILOOKUPRL -	Restrict lookup to one list
; 	- ANILOOKUPRC -	Restrict lookup to one campaign's lists
; 	- VID -		Add record with Vendor Lead Code received as argument 12
; 	- VIDLOOKUP - 	Lookup Vendor Lead Code received as argument 12 to find record in whole system
; 	- VIDLOOKUPRL -	Restrict lookup to one list (argument 12)
; 	- VIDLOOKUPRC -	Restrict lookup to one campaign's lists (argument 12)
; 	- VIDPROMPT - 	Prompt Vendor Lead Code to User with IVR to add record with Vendor Lead Code
; 	- VIDPROMPTLOOKUP - 	Prompt Vendor Lead Code to User with IVR to find record in whole system
; 	- VIDPROMPTLOOKUPRL -	Restrict lookup to one list
; 	- VIDPROMPTLOOKUPRC -	Restrict lookup to one campaign's lists
; 	- 3DIGITID - 	Enter 3 digit code to go to agent
; 	- 4DIGITID - 	Enter 4 digit code to go to agent
; 	- XDIGITID - 	Enter X digit code to go to agent(variable, i.e. 9DIGITID, 12DIGITID, etc...)
; 2. the method of searching for an available agent:
; 	- LO - Load Balance Overflow only (priority to home server)
; 	- LB - <default> Load Balance total system
; 	- SO - Home server only
; 3. the full name of the IN GROUP to be used in vicidial for the inbound call
; 4. the phone number that was called, for the log entry
; 5. the callerID or lead_id of the person that called(usually overridden)
; 6. the park extension audio file name if used
; 7. the status of the call initially(usually not used)
; 8. the list_id to insert the new lead under if it is new (and CID/ANI available)
; 9. the phone dialing code to insert with the new lead if new (and CID/ANI available)
; 10. the campaign_id to search within lists if CIDLOOKUPRC
; 11. the user to queue the call to for AGENTDIRECT in-group calls
; 12. vendor_lead_code if external mechanism like custom IVR is used to prompt user for ID
;
; inbound VICIDIAL call with CID delivery through T1 PRI
;exten => 1234,1,Answer                  ; Answer the line
;exten => 1234,2,AGI(agi-VDAD_ALL_inbound.agi,CID-----LB-----CL_GALLERIA-----7274515134-----Closer-----park----------999-----1)
;exten => 1234,3,Hangup










;exten => 6011,1,GoToIfTime(09:00-09:00|mon-sat|*|*?outbound,3010,1:outbound,6001,2)
exten => 6011,n,Ringing()
exten => 6011,n,Wait(1)
;exten => 6011,n,Playback(DelmedixIVR1)
exten => 6011,n,Answer()
;exten => 6011,n,AGI(agi-VDAD_ALL_inbound.agi,CID-----LB-----DELMEDIXINCOMING-----1244647560--------------------666-----1-----DELMEDIX----------
----------)
;exten => 6011,n,AGI(agi-VDAD_ALL_inbound.agi,CID-----LB-----SALESLINE-----01247102334--------------------999-----1-----DELMEDIX----------------
----)

exten => 6011,n,AGI(agi-VDAD_ALL_inbound.agi,CID-----LB-----SALESLINE-----01247102334--------------------999-----1-----TEST_IN------------------
--)
;exten => 6001,5,AGI(call_inbound.agi,-----DELMEDIXINCOMING-----1247112125--------------------666-----1-----DELMEDIX--------------------)
exten => 6011,n,Hangup()


; inbound VICIDIAL transfer calls [can arrive through PRI T1 crossover, IAX or SIP channel]
exten => _90009.,1,Answer                  ; Answer the line
exten => _90009.,2,Dial(${TRUNKloop}/9${EXTEN},,to)
exten => _90009.,3,Hangup
exten => _990009.,1,Answer                  ; Answer the line, Sometimes needs to be removed
exten => _990009.,2,AGI(agi-VDAD_ALL_inbound.agi,CLOSER-----LB-----CL_TESTCAMP-----7275551212-----Closer-----park----------999-----1)
exten => _990009.,3,Hangup
; DID forwarded calls
exten => _99909*.,1,Answer
exten => _99909*.,2,AGI(agi-VDAD_ALL_inbound.agi)
exten => _99909*.,3,Hangup


; barge monitoring extension
exten => 8159,1,ZapBarge
exten => 8159,2,Hangup

; ZapBarge direct channel extensions
exten => _86120XX,1,ZapBarge(${EXTEN:5})


exten => _X48600XXX,1,MeetMeAdmin(${EXTEN:2},T,${EXTEN:0:1})
exten => _X48600XXX,2,Hangup

exten => _X38600XXX,1,MeetMeAdmin(${EXTEN:2},t,${EXTEN:0:1})
exten => _X38600XXX,2,Hangup

exten => _X28600XXX,1,MeetMeAdmin(${EXTEN:2},m,${EXTEN:0:1})
exten => _X28600XXX,2,Hangup

exten => _X18600XXX,1,MeetMeAdmin(${EXTEN:2},M,${EXTEN:0:1})
exten => _X18600XXX,2,Hangup

exten => _55558600XXX,1,MeetMeAdmin(${EXTEN:4},K)
exten => _55558600XXX,2,Hangup
exten => 8300,1,Hangup

; astGUIclient conferences
exten => _86000[0-4]X,1,Meetme,${EXTEN}|q
; VICIDIAL conferences
exten => _86000[5-9]X,1,Meetme,${EXTEN}|F
exten => _8600[1-2]XX,1,Meetme,${EXTEN}|F
; quiet entry and leaving conferences for VICIDIAL (inbound announce and SendDTMF)
exten => _78600XXX,1,Meetme,${EXTEN:1}|Fq
; quiet monitor-only extensions for meetme rooms (for room managers)
exten => _68600XXX,1,Meetme,${EXTEN:1}|Fmq
; quiet monitor-only entry and leaving conferences for VICIDIAL (recording)
exten => _58600XXX,1,Meetme,${EXTEN:1}|Fmq

; voicelab exten
exten => _86009XX,1,Meetme,${EXTEN}|Fmq
; voicelab exten moderator
exten => _986009XX,1,Meetme,${EXTEN:1}



; park channel for client GUI parking, hangup after 30 minutes
;    create a GSM formatted audio file named "park.gsm" that is 30 minutes long
;    and put it in /var/lib/asterisk/sounds
exten => 8301,1,Answer
exten => 8301,2,AGI(park_CID.agi)
exten => 8301,3,Playback(park)
exten => 8301,4,Hangup 
exten => 8303,1,Answer
exten => 8303,2,AGI(park_CID.agi)
exten => 8303,3,Playback(conf)
exten => 8303,4,Hangup 

; park channel for client GUI conferencing, hangup after 30 minutes
;    create a GSM formatted audio file named "conf.gsm" that is 30 minutes long
;    and put it in /var/lib/asterisk/sounds
exten => 8302,1,Answer
exten => 8302,2,Playback(conf)
exten => 8302,3,Hangup

exten => 8304,1,Answer
exten => 8304,2,Playback(ding)
exten => 8304,3,Hangup

; default audio for safe harbor 2-second-after-hello message then hangup
;    create a GSM formatted audio file complies with safe harbor rules
;    and put it in /var/lib/asterisk/sounds then change filename below
exten => 8307,1,Answer
exten => 8307,2,Playback(execbusy2amp)
exten => 8307,3,Hangup

; this is used for playing a message to an answering machine forwarded from AMD in VICIDIAL
exten => 8320,1,AGI(VD_amd.agi,${EXTEN}-----YES)
exten => 8320,2,Hangup
exten => _8320*.,1,AGI(VD_amd.agi,${EXTEN}-----YES)
exten => _8320*.,2,Hangup

; use for selective CallerID hangup by area code(hard-coded)
exten => 8352,1,AGI(agi-VDADselective_CID_hangup.agi,${EXTEN})
exten => 8352,2,Playback(safe_harbor)
exten => 8352,3,Hangup

; this is used for sending DTMF signals within conference calls, the client app
;    sends the digits to be played in the callerID field
;    sound files must be placed in /var/lib/asterisk/sounds
exten => 8500998,1,Answer
exten => 8500998,2,Playback(silence)
exten => 8500998,3,AGI(agi-dtmf.agi)
exten => 8500998,4,Hangup

; multi-remote-monitor entry extensions
exten => 8162,1,Dial(${TRUNKblind}/34567890123456789,55,to)

exten => 34567890123456789,1,Answer
exten => 34567890123456789,2,Goto(monitor,s,1)

;#### VDAD STANDARD TRANSFER ENTRIES ####
; Below are the parameters needed for the agi-VDAD_ALL_outbound.agi script to be run properly
; 1. the method of call handling for the script:
; 	- NORMAL -	 	<default> Standard outbound routing to agent
; 	- TEST - 		For performance testing only
; 	- BROADCAST -	For no-agent broadcast dialing
; 	- SURVEY -		For survery question then on to agent
; 	- REMINDER -	Reminder campaign
; 	- REMINDX -		Reminder with transfer to agent
; 2. the method of searching for an available agent:
; 	- LB - <default> Load Balance total system
; 	- LO - Load Balance Overflow only (priority to home server)
; 	- SO - Home server only
; 3. the sound file to play when doing a SURVEY, REMINDER, REMINDX campaign
; 4. the acceptible dtmf digits for a SURVEY
; 5. the out-opt digit for a SURVEY (must be in the digit map)
; 6. the sound file to play for a SURVEY when transfering to an agent
; 7. the sound file to play for a SURVEY when DNCing the call
; 8. OPTIN or OPTOUT: if OPTIN call is only sent to agent with button press
;     if OPTOUT call is sent to agent if no button press at all
; 9. the status that is use for a SURVEY when someone opts out
;     if the status is DNC it will also add them to the internal dnc table

; VICIDIAL_auto_dialer transfer script for no-agent campaigns:
exten => 8364,1,Playback(sip-silence)
exten => 8364,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8364,3,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LB)
exten => 8364,4,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LB)
exten => 8364,5,Hangup

; VICIDIAL_auto_dialer transfer script:
exten => 8365,1,Playback(sip-silence)
exten => 8365,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8365,3,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----SO)
exten => 8365,4,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----SO)
exten => 8365,5,Hangup

; VICIDIAL_auto_dialer transfer script SURVEY at beginning:
exten => 8366,1,Playback(sip-silence)
exten => 8366,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8366,3,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMP-----LB)
exten => 8366,4,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMP-----LB)
exten => 8366,5,Hangup

; VICIDIAL_auto_dialer transfer script Load Balance Overflow:
exten => 8367,1,Playback(sip-silence)
exten => 8367,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8367,3,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LO)
exten => 8367,4,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LO)
exten => 8367,5,Hangup

; VICIDIAL_auto_dialer transfer script Load Balanced:
exten => 8368,1,Playback(sip-silence)
exten => 8368,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8368,3,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LB)
exten => 8368,4,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LB)
exten => 8368,5,Hangup

; VICIDIAL_auto_dialer transfer script AMD with Load Balanced:
exten => 8369,1,Playback(sip-silence)
exten => 8369,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8369,3,AMD(2000|2000|1000|5000|120|50|4|256) 
exten => 8369,4,AGI(VD_amd.agi,${EXTEN})
exten => 8369,5,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LB)
exten => 8369,6,AGI(agi-VDAD_ALL_outbound.agi,NORMAL-----LB)
exten => 8369,7,Hangup

; VICIDIAL auto-dial reminder script
exten => 8372,1,Playback(sip-silence)
exten => 8372,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8372,3,AGI(agi-VDADautoREMINDER.agi,${EXTEN})
exten => 8372,4,AGI(agi-VDADautoREMINDER.agi,${EXTEN})
exten => 8372,5,Hangup

; VICIDIAL SURVEY transfer script AMD with Load Balanced:
exten => 8373,1,Playback(sip-silence)
exten => 8373,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8373,3,AMD(2000|2000|1000|5000|120|50|4|256) 
exten => 8373,4,AGI(VD_amd.agi,${EXTEN})
exten => 8373,5,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMP-----LB)
exten => 8373,6,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMP-----LB)
exten => 8373,7,Hangup

; VICIDIAL SURVEY transfer script with Cepstral names:
exten => 8374,1,Playback(sip-silence)
exten => 8374,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8374,3,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMPCEP-----LB)
exten => 8374,4,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMPCEP-----LB)
exten => 8374,5,Hangup

; VICIDIAL SURVEY transfer script AMD with Cepstral variables:
exten => 8375,1,Playback(sip-silence)
exten => 8375,2,AGI(agi://127.0.0.1:4577/call_log)
exten => 8375,3,AMD(2000|2000|1000|5000|120|50|4|256)
exten => 8375,4,AGI(VD_amd.agi,${EXTEN})
exten => 8375,5,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMPCEP-----LB)
exten => 8375,6,AGI(agi-VDAD_ALL_outbound.agi,SURVEYCAMPCEP-----LB)
exten => 8375,7,Hangup



; PERFORMANCE TESTING
exten => _999XXXXXX1,1,Answer
exten => _999XXXXXX1,2,Wait(2)
exten => _999XXXXXX1,3,Playback(vicidial-welcome)
exten => _999XXXXXX1,4,Hangup


;aditya
exten => _913522699999.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _913522699999.,n,Dial(SIP/913522699999@your_gateway_name,,Tto)
exten => _913522699999.,n,System(echo 'Call from ${CALLERID(name)} at  ${CALLERID(number)}' >> /tmp/test)
exten => _913522699999.,n,Dial(DAHDI/g0/9717589888)
exten => _913522699999.,4,Hangup






exten => _999XX11112,1,Wait(2)
exten => _999XX11112,2,Answer
exten => _999XX11112,3,Playback(ss-noservice)
exten => _999XX11112,4,Playback(vm-goodbye)
exten => _999XX11112,5,Hangup

exten => _999XX18112,1,Wait(2)
exten => _999XX18112,2,Answer
exten => _999XX18112,3,Playback(vtiger-fax)
exten => _999XX18112,4,Playback(vtiger-fax)
exten => _999XX18112,5,Hangup

exten => _999XX19112,1,Wait(2)
exten => _999XX19112,2,Answer
exten => _999XX19112,3,Playback(vtiger-email)
exten => _999XX19112,4,Playback(vtiger-email)
exten => _999XX19112,5,Hangup

exten => _999XXXX112,1,Wait(5)
exten => _999XXXX112,2,Answer
exten => _999XXXX112,3,Playback(demo-instruct)
exten => _999XXXX112,4,Playback(demo-instruct)
exten => _999XXXX112,5,Hangup

exten => _999XXXXXX2,1,Wait(8)
exten => _999XXXXXX2,2,Answer
exten => _999XXXXXX2,3,Playback(demo-instruct)
exten => _999XXXXXX2,4,Hangup

exten => _999XXXXXX3,1,Set(PRI_CAUSE=1)
exten => _999XXXXXX3,2,Hangup

exten => _999XXXXXX4,1,Set(PRI_CAUSE=27)
exten => _999XXXXXX4,2,Hangup

exten => _999XXXXXX5,1,Wait(60)
exten => _999XXXXXX5,2,Hangup

exten => _999XXXXXX6,1,Wait(10)
exten => _999XXXXXX6,2,Answer
exten => _999XXXXXX6,3,Playback(demo-instruct)
exten => _999XXXXXX6,4,Hangup

exten => _999XXXXXX7,1,Wait(12)
exten => _999XXXXXX7,2,Answer
exten => _999XXXXXX7,3,Playback(demo-enterkeywords)
exten => _999XXXXXX7,4,Hangup

exten => _999XXXXXX8,1,Set(PRI_CAUSE=17)
exten => _999XXXXXX8,2,Hangup

exten => _999XXXXXX9,1,Wait(6)
exten => _999XXXXXX9,2,Answer
exten => _999XXXXXX9,3,Playback(demo-abouttotry)
exten => _999XXXXXX9,4,Hangup

exten => _999XXXXXX0,1,Wait(5)
exten => _999XXXXXX0,2,Answer
exten => _999XXXXXX0,3,Playback(vm-goodbye)
exten => _999XXXXXX0,4,Hangup

exten => 99999999999,1,Answer
exten => 99999999999,2,Playback(conf)
exten => 99999999999,3,Playback(conf)
exten => 99999999999,4,Playback(conf)
exten => 99999999999,5,Playback(conf)
exten => 99999999999,6,Playback(conf)
exten => 99999999999,7,Playback(conf)
exten => 99999999999,8,Playback(conf)
exten => 99999999999,9,Playback(conf)
exten => 99999999999,10,Playback(conf)
exten => 99999999999,11,Playback(conf)
exten => 99999999999,12,Playback(conf)
exten => 99999999999,13,Playback(conf)
exten => 99999999999,14,Hangup


[monitor]
exten => h,1,DeadAGI(agi://127.0.0.1:4577/call_log--HVcauses--PRI-----NODEBUG-----${HANGUPCAUSE}-----${DIALSTATUS}-----${DIALEDTIME}-----${ANSWE
REDTIME})

exten => s,1,Set(TIMEOUT(digit)=10)
exten => s,n,Set(TIMEOUT(response)=10)
exten => s,n,Set(MEETME_EXIT_CONTEXT=monitor_exit)
exten => s,n,Background(vm-extension) ; need audio prompt.
exten => s,n,WaitExten(10)

exten => i,1,Goto(monitor_exit,s,1)
exten => #,1,Goto(monitor_exit,s,1)
exten => t,1,Goto(monitor_exit,s,1)

exten => _8[0-2]XX,1,Meetme(8600${EXTEN:1},mqX) ; Listen
exten => _99[0-2]XX,1,Meetme(8600${EXTEN:2},X)  ; Barge

[monitor_exit]
exten => h,1,DeadAGI(agi://127.0.0.1:4577/call_log--HVcauses--PRI-----NODEBUG-----${HANGUPCAUSE}-----${DIALSTATUS}-----${DIALEDTIME}-----${ANSWE
REDTIME})

exten => _X,1,Goto(monitor,s,1)

exten => i,1,Goto(monitor,s,1)
exten => #,1,Goto(monitor,s,1)
exten => t,1,Goto(monitor,s,1)
You have new mail in /var/spool/mail/root
[root@go asterisk]# 




---------------------------------------------------------------------------





;adityadroozo1
exten => _5677777XX.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _5677777XX.,n,MixMonitor(/var/www/html/delmedix/${STRFTIME(${EPOCH},,'%Y%m%d-%H%M%S-')}${CALLERID(name)}-${CALLFILENAME}.wav)
exten => _5677777XX.,n,Dial(SIP/${EXTEN}@bsnlout,,tTo)
exten => _5677777XX.,n,Hangup





;aditya
exten => _913522699999.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _913522699999.,n,Dial(SIP/913522699999@your_gateway_name,,Tto)
exten => _913522699999.,n,System(echo 'Call from ${CALLERID(name)} at  ${CALLERID(number)}' >> /tmp/test)
exten => _913522699999.,n,Dial(DAHDI/g0/9717589888)
exten => _913522699999.,4,Hangup






;aditya
exten => _913522699999.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _913522699999.,n,Dial(SIP/913522699999@your_gateway_name,,Tto)
exten => _913522699999.,n,System(echo 'Call from ${CALLERID(name)} at  ${CALLERID(number)}' >> /tmp/test)
exten => _913522699999.,n,Dial(DAHDI/g0/9717589888)

;aditya
exten => _5677777XX.,n,Dial(SIP/${EXTEN}@bsnlout,,tTo)
exten => _913522699999.,n,Dial(SIP/56777779717589888@bsnlout,,tTo)

:aditya

exten => _913522699999.,4,Hangup









;aditya
exten => _913522699999.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _913522699999.,n,Dial(SIP/913522699999@your_gateway_name,,Tto)
exten => _913522699999.,n,System(echo 'Call from ${CALLERID(name)} at  ${CALLERID(number)}' >> /tmp/test)
exten => _913522699999.,n,Dial(DAHDI/g0/9717589888)

;aditya
;exten => _5677777XX.,n,Dial(SIP/${EXTEN}@bsnlout,,tTo)
exten => _913522699999.,n,Dial(SIP/56777779717589888@bsnlout,,tTo)
:aditya

exten => _913522699999.,4,Hangup



# aditya for forwarding to multiple numbers below




















;aditya
exten => _913522699998.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _913522699998.,n,Dial(SIP/913522699999@your_gateway_name,,Tto)
exten => _913522699998.,n,System(echo 'Call from ${CALLERID(name)} at  ${CALLERI
D(number)}' >> /tmp/test)
;exten => _913522699998.,n,Dial(DAHDI/g0/9717589888)

;aditya
;exten => _5677777XX.,n,Dial(SIP/${EXTEN}@bsnlout,,tTo)
exten => _913522699998.,n,Dial(SIP/56777779717589888@bsnlout&SIP/56777777042834976@bsnlout,,tTo)
exten => _913522699998.,n,Wait(3)
exten => _913522699998.,n,Dial(SIP/56777777042834976@bsnlout,,tTo)

;bhavin
;exten => _913522699998.,n,Dial(SIP/56777779891787927@bsnlout,,tTo)
;exten => _913522699998.,n,Dial(SIP/56777779999124872@bsnlout,,tTo)
;bhavin

;aditya

exten => _913522699998.,6,Hangup



------------------------









;aditya
exten => _913522699998.,1,AGI(agi://127.0.0.1:4577/call_log)
;exten => _913522699998.,n,Dial(SIP/913522699999@your_gateway_name,,Tto)
exten => _913522699998.,n,System(echo 'Call from ${CALLERID(name)} at  ${CALLERI
D(number)}' >> /tmp/test)
;exten => _913522699998.,n,Dial(DAHDI/g0/9717589888)

;aditya
;exten => _5677777XX.,n,Dial(SIP/${EXTEN}@bsnlout,,tTo)
exten => _913522699998.,n,Dial(SIP/56777779717589888@bsnlout&SIP/56777777042834976@bsnlout,,tTo)
;exten => _913522699998.,n,Wait(3)
;exten => _913522699998.,n,Dial(SIP/56777777042834976@bsnlout,,tTo)

;bhavin
;exten => _913522699998.,n,Dial(SIP/56777779891787927@bsnlout,,tTo)
;exten => _913522699998.,n,Dial(SIP/56777779999124872@bsnlout,,tTo)
;bhavin

;aditya

exten => _913522699998.,4,Hangup
