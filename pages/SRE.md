---
title: SRE
---

- 

- Site reliability engineering
	 - In het algemeen is een SRE-team verantwoordelijk voor beschikbaarheid, latentie, prestaties, efficiëntie, verandermanagement, monitoring, reactie op noodsituaties en capaciteitsplanning of een subset hiervan.

	 - Het uiteindelijke doel van SRE's is om, zoals Google het uitdrukt, binnen een jaar hun eigen baan weg te automatiseren. Een belangrijke manier om dit te doen is het bouwen van zelfbedieningstools voor gebruikersgroepen die afhankelijk zijn van hun diensten. Bijvoorbeeld  automatische levering van testomgevingen, logboeken en statistische visualisatie. Hierdoor wordt het uitvoerende werk voor alle partijen minder. De ontwikkelaars kunnen zich vervolgens volledig richten op de ontwikkeling van software. De SRE kan zich daarna richten op de volgende automatiseringslag, waarmee het proces weer van voor af aan begint.

	 - Zet geen container stuk neer.

	 - Wel development (openshift)

	 - Schaalbaarheid

	 - Post-mortum, probleem wat nooit eerder is voorgekomen, wat was het probleem, hoe kunnen we er voor zorgen dat het nooit meer gebeurt en monitoren dat het nooit meer gebeurt.

	 - Dag
		 - UNit tests oplossen

		 - Database opzetten

		 - 

		 - Fouten in de toekomst vroeg voorkomen.

		 - 

	 - Monitoring
		 - https://prometheus.io/

	 - 

- [[SLO]]
	 - https://linuxacademy.com/

	 - Needs [[SLO]]'s service-level objectives 
		 - Getting Started with SRE - Stephen Thorne, Google: https://www.youtube.com/watch?v=c-w_GYvi0eA

		 - SLO set a goal for how well the system should behave

		 - Specifically tracking custoimer experience

		 - if customer happy the the SLO is being met 
			 - SLO EXAMPLE:
				 - uptaime of 99,9% a momth

				 - 99,99 http reuqests 200 OK

				 - 50% of HTTP requests returned under 300ms

				 - 99% of log entries processed under 5 min

			 - SLA is de tegenhanger van een SLO, hir wordt je accountable gehouden voor de fouten die je maakt in je SLO. Qonsequenses

		 - ERROR  BUDGET POLICY https://youtu.be/c-w_GYvi0eA?t=506
			 - How reliable do you want to be?

			 - Error budget procent requests, monitoring van fouten na deployments.
				 - Error budget policys
					 - Totdayte de applicatie weer up to par is kan pas weer nieuwe features gpuished worden.

					 - 
