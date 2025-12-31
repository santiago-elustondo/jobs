

email
assets
github organization (conexis-vms)
ad-hoc-reports
conexis-vms
conexis-tools
conexis-vms-dev
will provide free support
andres (and nico if continues) whenever they reach out directly
anyone else in conexis or in soluntech as requested by conexis team
tn
reports app
* auth
* deploy
admin-tools app
* rss
* monitor
password reset
new_arch
monorepo (microservices / microfrontends)
can deploy individually or import as packages (front/back)
flexes
live support (firebase/websockets)
superadmin can see online users
can impersonate users
can do audio chat (with a voice wave animation and profile picture) through app
admin can see what route they are on or turn on screenshots once in a while
announcement banners (with emojis / fireworks) that will show up once per user or until dismissed
pulsating highlight, arrows and other ways to focus attention
can be posted by buyer admins, msp admins, etc
announce 
new features
somebody’s birthday lol
this could be done automatically 
port the ad hoc reports app into cordova
ad hoc responsiveness
auto regression plan, they click around, but we generate code that we can review and edit.
use AI to parse through all the text she generated and put together a playbook
*** admin tools should be deployed into our own thing. 
*** john should get an auto email every day saying what times we checked at and what happened
env server hot config via admin tools
** rich text editing with images and videos for job descriptions (preserve caloptima’s descriptions)
** usage metrics over time, since we also know who is online we can reach out and either try to support or ask for feedback. 
** whitelabel (first show it on reports)
move the update user app into just another UI, the problem isnt writing uis, that might actually be easier than cli, the problem is devops, you want to deploy fast and they can use it. reports could be an MFE / microapp as well in that same way
	
multi-tenant
QA regression
we need dedicated environment (dev)
at first not automated, we trigger it
config service
global
tenant 
objective
whitelabel
callouts
complejidad: van a ser parecido
labmda/kafka hay q tener cuidado con devex
assumptions 
tenants: msp or self serve buyer
factors for tenant capacity
data size
change requests (deploys)
num user
todo feats
general SSO configurable, 2 step login process
superuser 
impersonate user
update config
*stephanie KT go through her work and videos
*super users
global server config
reports
last reports (andres)
backend 
	design (scalable and testable)
	implementation in place, not a lot of tech debt involved
	testing via pure auto and possibly point and click
frontend 
	design (simple, hold tenant and tenant config in service)
		case by case implementation strategy: read from config service and apply logic.
		allowed to break architecture pattern as long as: simpler or better and discussed
	no testing
multi-tenant meet
https://www.notion.so/soluntech/Variations-for-CalOptima-671b22bf7de4493b88591371c0a475d1
*** get recording
* e2e testing 
search for point and click tool for live in env (start with empty db every time)
also write code system without fronend to fill in data
write down current related technical debt
rewrite minimal relevant front end parts to handle this better and more simple(not css responsive but with new pattenrn)
global server configurations table, manageable via super user / admin tools ()
npm run find-user -- --input='santi'
npm run test-pass -- --user='742cb609-6e5c-44ba-abca-31c2583514dc' --pass=‘Cl’
npm run set-pass -- --user='<user_id>' --pass='<password>'
npm run send-email -- --user='<user_id>' --subject='<subject>'
dayana andres meet
muy atento
learning curve
pre-meet
code
2) pageup
admin tools
refactor
2) monitoring
4) reports
2) monitoring
onboarding
1) labels
3) ? attachments
strategy
process (velocity / collaboration)
roadmap
architecture
———
conexis-tools
find user (email / name)
set user password
activate/deactivate user
send email to user(s)
send email to all suppliers
_
switch back to in progress 
who was it
hiring managers cant accept candidates
set as hiring manager
should be buyer admin
wednesday
** admin/support
* user reset password
* email batching
* emails to suppliers
* monitoring 
write to special log file using structured format
michelle ideas + emails
neisser writes download endpoint
* PR: email when rss job
* PR: auto-watch for jobs
* add jobs to jobs_rss
** hyperlink label
* sub/unsub user to different types email notifications
via conexis tools (later via UI)
andres
out of town, good guy
do
conexis: admin/support tools
hyperlink label
conexis: email
batching
add up total sent
calculate total emails that should have been sent
should michelle have gotten an email (algun supplier emial. NO)
conexis: check rss feed
** sg: respond to sean
(later) conexis: users can turn off notifications for things
candidate getting emails to log into conexis
** conexis: timeline / points / sprints (measure)


datasets
select collection
filters (only single field)
select field (types shown)
select comparator and input value
? calculated fields
? groups
views
data table
pie
time
bars
text with values (like totals, etc)
exports
csv
pdf
emails
automate
updateable fields (for example change dates)
emails
reports
dates for time graph
reports: considerations
calculated fields using info within record
calculated aggregate fields
totals (this is a separate view or optional part within view)
group (this could be done by view, or.. the whole thing is a view, no?)
view-first: select a view, then: for each view
select collection
))))))))))))))
Node.js v18.17.1
(base) santi@santiagos-MBP-2 rss % node ./index.js
[
  [
    '20c6a3df-31c0-4ba6-80fe-65c5e2b25de9',
    'Manager, PACE Center',
    2024-03-25T16:00:00.000Z
  ],
  [
    '058562b4-bb66-4ea1-a95b-2c59a757f880',
    'Data and Reporting Analyst – Lead',
    2024-03-25T16:00:00.000Z
  ]
]
pers
singtrix
spotify collab + code
spark live
—— 
CONEXIS TODO
** ad hoc
job description editor
** console tools for pulling in jobs
enable SSO for conexis users
auth (MSP super admin)
disable SSO for suppliers  (creation screens and login)
can we keep for conexis
user mngmt: reset password / send emails utility (terminal)
record users having issues logging in. send them a question (“having issues logging in? send message”)
** activate all caloptima hiring managers (bulk actions for users)
what is “activated”? is there an issue? can u activate? what does it mean for SSO
detect users online
make a new type of support/admin user
ask for help thingy (some free plugin) (what about logrocket?)
email save
email copy -> caloptima to conexis
andres solution
login errors: disable SSO as an option
login errors: activating an account as an admin (wayne)
finish rss
finish reports
playing possum
******** email sending interface
** automated test
emails: save
pageup: local script
reports: wait till end of day
%%%%%%
other
pay jameel
sectorgrowth follow up
rn
email batching (send emails UI)
? user batch import (ask day)
pageup
reports
columns
4th report
sorting, filtering
computed:
@todo (*later) LOA: calendar days
hide reports button
sso (kenny email)
wayne’s thing (ask andres)
&&&&&&&&&&&&&&
code
reports
O add columns (need backend)
filters (as defined by michelle)
wayne’s thing: https://trello.com/c/iagbNepj/189-disable-approve-button-for-hiring-managers-on-submission-page
++++++++++++
bad religion
propaghandi


* TN (after): 
wayne’s thing
kenny email
missing cols
length of assignment
exclusion
* start date is special, needs logic (computed field)
——
tn
X expiration dates
dates bug
invoice
X hyperlinks
reports
O missing columns
missing report
X contract ids in other 2
X exports
hide tab icon
make UI more consistent
tmrw
TALK TO/ABOUT ANDRES
scripts for snapshot + clearing
* email batching
pageup
domain
email kenny sso
update env var
dns change
check for urls (in code and db)
later
migration / multitenant
auth, worker onboarding
todo
sso
pageup
reports
email batch
* webdriver visual testing
* domain
———
shop
alien food
salads / lemonv (other food)
guitar strings
booze
prescription
tonight
env var defaults, so we can just deploy SSO everywhere, with our provider by default
SSO UI transitions 
**invoice!!**
fixing bugs and updating devops, deploys, deploying to different environment.
emails went down last week but we thought it was
todo post-launch
sso: use something better than get param
there must be a better way to do this whole sso token thing
*** https://github.com/node-saml/passport-saml/issues/157 
right now we’re exposing token to everyone
URGENT: the auth records stay forever!! terrible!
* improve UI with a success screen
pageup
ssn encrypt
working with devops to get everything deployed
conexis dev env cant deploy without also breaking qa and staging
ci is broken and prs are spinning, emails not sending (confusing, needs easier rollbacks)
memory heap exceptions
we cant update env vars
redeploying manually
he’s telling me to delete passwords, making himself a bottleneck
the wrong thing gets deployed over and over again
test runner hangs and doesnt finish
deployed onto dev yesterday to test SSO, and this morning it was undeployed and he was busy "we should just follow the regular flow"
sonarqube stopping prs and tsking forever
he does not want me to 
e2e test fails that are unrelated hold up prs. key conflicts in database. each merge gets delayed by a whole day (and u usually need more than one merge per ticket). also these are blockers, usually only one dev is familiar with the issue.
i wasted a lot of time with it, and some tickets are just sitting there waiting for unblock.
stops agustins issues too. 
very common to have long meetings and spikes into ci problems


story: my clever move to ask for dev control by deploying branch, then deploy onto dev first out simulator, and then only change the env vars to minimize chance of fail. pero cada update toma mil anios y depende de blanco. as a dev you want to optimize for things that affect risk or speed, and this is possible
complain about project
the main reason we are encountering this resistance is the project
we can improve this stuff
i meant to bring it up on wednesday
its not the 
is this is not a usual state of affairs. its too much work to get shit done, too uncertain, too many random bugs. bugs rae too hard (like email bug, and frontend filters) and shit is too hard to test
———
michelle.rhodes@conexis.io
andres.perdomo@conexis.io
Messi_10!!

QA: https://qa.conexissoftware.com/
Staging: https://staging.conexisvms.com
PROD: https://prod.conexissoftware.com/
MSP Level
MSP Administrator: jheidy@soluntech.com / Clave123*
Program Manager: jheidy+prog@soluntech.com / Clave123*
Program Representative: conexis+programrep@soluntech.com / Clave123*
Program Representative: jheidy+programrep@soluntech.com / Clave123*
MSP Finance: jheidy+mspfinance@soluntech.com / Clave123*
BUYER Level
Buyer Administrator: jheidy+buyerad@soluntech.com / Clave123*
Buyer administrator (self-served): jheidy+badss@soluntech.com / Clave123*
Hiring Manager (self-served): jheidy+selfhir@soluntech.com / Clave123*
Hiring Manager (MSP buyer): jheidy+hir@soluntech.com / Clave123*
Recruiter(Self-served): jheidy+recnew@soluntech.com / Clave123*
Buyer Finance : jheidy+bf@soluntech.com / Clave123*
Buyer finance (self-served): estefania+bfinancess@soluntech.com / Clave123*
Delegate: jheidy+delegatetest@soluntech.com / Clave123*
SUPPLIER Level
Supplier administrator: jheidy+supadministrator@soluntech.com / Clave123*
Account manager: jheidy+pmconexis@soluntech.com / Clave123*
Supplier Finance: jheidy+sfin@soluntech.com / Clave123*
WORKER Level
Worker: jheidy+candidate@yopmail.com / Clave123*
issues: 
JobResource methods return IData.DataJobs[] not Response<IData.DataJobs[]>
theres a thunk middleware that wraps to make that type
should be job[] or jobs[]
queued tasks batch job uses server to run them…
different dashboard component for each user type doing pretty much same thing but written differently causing bugs
sometimes theyre not even used, for some user roles it doesnt actually use the corresponding dashboard
in rendering buyer-invoices list, so many times we seem to apply filters that dont do anything, so many red herrings trying to find where filter happens
same with generating columns and stuff
the filtering actually happens inside antd table also
import { parseString } from 'xml2js';
import * as csv from 'node-csv';
import * as pg from 'pg';
import { v4 as uuidv4 } from 'uuid';
const parser = csv.createParser();
// @todo: .env var
const CALOPTIMA_TENANT = 9;
const go = async () => {
  // const res = await fetch(
  //   'https://careers.pageuppeople.com/1150/cw/en-us/latest_jobs.rss',
  // );
  // const xml = await res.text();
  // parseString(xml, (err, feed) => {
  //   console.log('err', err);
  //   console.log('feed', feed.rss.channel);
  // });
  const pageupJobs: any = await new Promise((resolve) => {
    parser.parse(csvStr, (err, data) => {
      const columns = data[0];
      const rows = data.slice(1);
      const pageupJobs = rows.map((row) =>
        columns.reduce((job, col, i) => ({ ...job, [col]: row[i] }), {}),
      );
      resolve(pageupJobs);
    });
  });
  console.log(pageupJobs[pageupJobs.length - 1]);
  const conexisJobs = pageupJobs.map((puj) => {
    return {
      tenant: CALOPTIMA_TENANT,
      job_title: puj.title,
      job_description: puj.description,
      job_comments: puj.jobDescription,
      created_on: puj.pubDate,
      date_of_submission: puj.pubDate,
      status: 'Unposted',
    };
  });
  const j = conexisJobs[conexisJobs.length - 1];
  console.log(j);
  // Create a PostgreSQL client
  const client = new pg.Client({
    user: 'conexisdev',
    host: 'conexis-dev.c4bh62ekgxbe.us-east-1.rds.amazonaws.com',
    database: 'testdb',
    password: 'conexisdev',
    port: 5432,
  });
  await client.connect();
  const query = `
    INSERT INTO jobs (id, buyer, id_tenant, job_title, job_description, job_comments, status)
    VALUES ($1, $2, $3, $4, $5, $6, $7)
`;
  const id = uuidv4();
  console.log(id);
  const values = [
    id,
    '1b671a64-40d5-491e-99b0-da01ff1f3347',
    9,
    j.job_title,
    j.job_description,
    j.job_comments,
    'Unposted',
  ];
  try {
    await client.query(query, values);
    console.log('Query executed successfully.');
  } catch (error) {
    console.error('Error executing query:', error);
  }
  // const title = item.title;
  // const link = item.link || null;
  // const description = item.description || null;
  // const pubDate = item.pubDate || null;
  // const updated = item['a10:updated'] || null;
  // const category = item['job:category'] || null;
  // const refNo = item['job:refNo'] || null;
  // const jobDescription = item['job:description'] || null;
  // const applyLink = item['job:applyLink'] || null;
  // const closingDate = item['job:closingDate'] || null;
  // const location = item['job:location'] || null;
  // const workType = item['job:workType'] || null;
  // const subCategory = item['job:subCategory'] || null;
  // const businessLayer1 = item['job:businessLayer1'] || null;
};
//——
const FRONT_ORIGIN = 'https://9933fcef42a7.ngrok.app';
const BACK_ORIGIN = 'https://c088e820656a.ngrok.app';
const CALOPTIMA_TENANT_ID = '9';
// CONEXIS
// const SAML_ENTRY_POINT_AZURE_CALOPTIMA = 'https://login.microsoftonline.com/ec718c8e-48a4-4a23-b86d-810e87438277/saml2'
// const SAML_ISSUER_AZURE_CALOPTIMA = '29749540-7b45-42f4-8cc1-11391415cec3'
// const SAML_CERT_AZURE_CALOPTIMA = 
// CALOPTIMA
const SAML_ENTRY_POINT_AZURE_CALOPTIMA =
  'https://launcher.myapps.microsoft.com/api/signin/d0385da9-b7fa-4cd0-ace2-0f7ce28cc591?tenantId=819fa30a-b4d6-4604-bc10-c0f5019ba861';
const SAML_ISSUER_AZURE_CALOPTIMA = 'd0385da9-b7fa-4cd0-ace2-0f7ce28cc591';
const SAML_CERT_AZURE_CALOPTIMA =

