---
title: Smartblocks
---

- Workbench example:
	 - [Smartblocks: command reference by category | Roam42 (roamjs.com)](https://roamjs.com/extensions/roam42/smartblocks:_command_reference_by_category)

	 - https://www.loom.com/share/e3a28134e96f47629cde420152d26f6c

	 - [Issues · dvargas92495/SmartBlocks · GitHub](https://github.com/dvargas92495/SmartBlocks/issues)

- #42SmartBlock test
	 - <%OPENPAGE:Gijs test%>
		 - asdasdasdasd

		 - asdasdasdasdasdasd

- 

- #42SmartBlock Plan day
	 - <%SIDEBARWINDOWOPEN:[[THIS MONTH]]%>

	 - <%SIDEBARWINDOWOPEN:[[THIS WEEK]]%>

	 - <%SIDEBARWINDOWOPEN:<%DATE:yesterday%>%>

	 - <%NOBLOCKOUTPUT%>

- #42SmartBlock WaitingFor
	 - Waitingfor <%DATE:IN one week%>

- #42SmartBlock Create project <%GLOBAL%>
	 - <%SET:ProjectName,<%INPUT:Whats the project name?%>%><%NOBLOCKOUTPUT%>

	 - <%SIDEBARWINDOWOPEN:<%GET:ProjectName%>,GOTOBLOCK 2%>
		 - dfsdfsdfsdf

- 
	 - **Tags:** #[[Projects]] #[[ShopWorks]]

	 - **Date created:** <%DATE: Today%>

	 - **Completed Date:** 

	 - **Status:** 

	 - **Related Goals:** 

	 - **People:**

	 - 

	 - **Project todos:**
		 - {{[[query]]: {and: [[TODO]] [[<%GET:ProjectName%>]]}}}

	 - <%CLEARVARS%>

- 

- #42SmartBlock Start Meeting
	 - <%INPUT:Whats the meeting about?%> <%CURSOR%> #Meeting 
		 - **Attendees:** 

		 - 

		 - **NOTES:**

		 - 

		 - **TODOS:**

		 - 

- #42SmartBlock Maaltijdplanner
	 - [[Weekplanning eten]]
		 - **Gerechten zoeken:**
			 - https://www.ah.nl/allerhande/recepten/R-L1383829454750/wat-eten-we-vandaag

			 - https://www.rijnakookt.com/

			 - https://www.eendagsrestaurant.nl/product/vrijdag-menu/?s=09

		 - **Dagen:**

		 - Zaterdag <%DATE:Saturday%>

		 - Zondag  <%DATE:Sunday%>

		 - Maandag <%DATE:Next Monday%>

		 - Dinsdag <%DATE:Next Tuesday%>

		 - Woensdag <%DATE:Next Wednesday%>

		 - Donderdag <%DATE:Next Thursday%>

		 - Vrijdag <%DATE:Next Friday%>

		 - Zaterdag <%DATE:Next Saturday%>

		 - Zondag <%DATE:Next Sunday%>

- #42SmartBlock create day
	 - <%SIDEBARWINDOWOPEN:[[THIS WEEK]]%>

	 - **START:**
		 - TODO Plan day, check calendar

		 - TODO Empty todoist inbox

	 - {{embed  ((((d827ccd1-560e-481a-87af-1ca792fb12f9))))}}

	 - **MITS**
		 - 

	 - **TODOS**
		 - 

	 - **NOTITIES:**

- #42SmartBlock new Customer <%GLOBAL%>
	 - <%SET:CustomerName, <%INPUT:Whats the customer name?%>%><%NOBLOCKOUTPUT%>

	 - <%SIDEBARWINDOWOPEN:<%GET:CustomerName%>%><%GOTOBLOCK:-1%><%NOBLOCKOUTPUT%>

	 - 

	 - **Tags:** #Customers

	 - **Phone Number:**

	 - **Date created:** <%DATE: Today%>

	 - **Email:**

	 - **Stakeholders:**

	 - **Projects:**

	 - 

	 - <%CLEARVARS%><%NOBLOCKOUTPUT%>
