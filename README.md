# TareaBD
##Primer MER
´´´
--employee table
CREATE TABLE employee(
	eid INTEGER PRIMARY KEY,
	phone VARCHAR(200)
);
--email table
CREATE TABLE email(
	eid INTEGER,
	text VARCHAR(200) PRIMARY KEY,
	FOREIGN KEY (eid) REFERENCES employee(eid)
);
--login table
CREATE TABLE login(
	eid INTEGER,
	username VARCHAR(200) PRIMARY KEY,
	password VARCHAR(200),
	FOREIGN KEY (eid) REFERENCES employee(eid)
);
--departament table
CREATE TABLE departament(
	did INTEGER PRIMARY KEY,
	name VARCHAR(200),
	description VARCHAR(500)
);
--role table
CREATE TABLE role(
	rid INTEGER PRIMARY KEY,
	name VARCHAR(200),
	description VARCHAR(500)
);
--employeeDepartament table
CREATE TABLE employeeDEPARTAMENT(
	eid INTEGER,
	did INTEGER,
	FOREIGN KEY (eid) REFERENCES employee(eid),
	FOREIGN KEY (did) REFERENCES departament(did)
);
--employeeRole table
CREATE TABLE employeeRole(
	eid INTEGER,
	rid INTEGER,
	FOREIGN KEY (eid) REFERENCES employee(eid),
	FOREIGN KEY (rid) REFERENCES role(rid)
);
´´´
##Segundo MER
´´´
-- publisher table 
CREATE TABLE publisher(
	name VARCHAR(200) PRIMARY KEY,
	address VARCHAR(200),
	phone VARCHAR(30)
);
--book table
CREATE TABLE book(
	bid INTEGER PRIMARY KEY,
	name VARCHAR(200),
	title VARCHAR(200),
	FOREIGN KEY (name) REFERENCES publisher(name)
);
--authorName table
CREATE TABLE authorName(
	anid INTEGER PRIMARY KEY,
	bid INTEGER,
	authorName VARCHAR(200),
	FOREIGN KEY (bid) REFERENCES book(bid) ON DELETE CASCADE
);
--borrower table
CREATE TABLE borrower(
	cid INTEGER PRIMARY KEY,
	name VARCHAR(200),
	addres VARCHAR(200),
	phone VARCHAR(200)
);
--brach table
CREATE TABLE branch(
	brid INTEGER PRIMARY KEY,
	name VARCHAR(200),
	addres VARCHAR(200)
);
--copies table
CREATE TABLE copies(
	bid INTEGER,
	brid INTEGER,
	nocopies BOOLEAN,
	FOREIGN KEY (bid) REFERENCES book(bid),
	FOREIGN KEY (brid) REFERENCES branch(brid)
);
--loans table
CREATE TABLE loans(
	bid INTEGER,
	brid INTEGER,
	cid INTEGER,
	dateOut DATE,
	dueDate DATE,
	FOREIGN KEY (bid) REFERENCES book(bid),
 	FOREIGN KEY (brid) REFERENCES branch(brid),
	FOREIGN KEY (cid) REFERENCES borrower(cid)
);
´´´
