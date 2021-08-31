### SQL.
```sql
/*Get the ClaimDetails Data from CSV*/
CREATE TABLE ClaimDetails (
    ClaimsDetailsID INT,
    AnimalID INT,
    BeneficiaryID VARCHAR(40),
    VetID VARCHAR(20),
    ServiceID VARCHAR(20),
    IncidentDate DATE,
    FeePaymentDate DATE,
    FeeSubmitted INT,
    ReasonableFee INT,
    VetFeePaid FLOAT,
    BeneficaryFeePaid FLOAT
);

LOAD DATA LOCAL INFILE "/home/sriq/Downloads/data.csv" INTO TABLE pets.ClaimDetails
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 3 LINES
(ClaimsDetailsID,AnimalID,BeneficiaryID,VetID,ServiceID,@IncidentDate,@FeePaymentDate,FeeSubmitted,ReasonableFee,VetFeePaid,BeneficaryFeePaid)
set IncidentDate = STR_TO_DATE(@IncidentDate,'%m/%d/%Y'), FeePaymentDate = STR_TO_DATE(@FeePaymentDate,'%m/%d/%Y');


/*Get the AnimalDetails Data from CSV*/
CREATE TABLE AnimalDetails (
    AnimalID INT,
    Spieces VARCHAR(40),
    Name VARCHAR(20));

LOAD DATA LOCAL INFILE "/home/sriq/Downloads/animal.csv" INTO TABLE pets.AnimalDetails
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 3 LINES
(AnimalID,Spieces,Name);
```
