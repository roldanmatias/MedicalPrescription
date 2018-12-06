# MedicalPrescription
Blockchain Medical Prescription Project

Red entre médicos, pacientes, farmacias e industria farmacétutica.

Permite crear, enviar y rastrear recetas médicas electrónicas

## Problema:

- Falsificación prescripciones médicas.
- Adquisición estas recetas apócrifas

Para verificar una prescripción médica se requiere que el personal de las farmacias esté plenamente capacitado para revisar que estén firmadas, que los datos tanto del médico como del paciente estén completos y comprobar que la matrícula profesional coincida con la del especialista que emitió la prescripción.

Las prescripciones en las farmacias, pueden ser escaneadas por alguien para hacer investigaciones de mercado. Las cadenas de farmacias grandes venden estos datos a compañías trasnacionales quienes deben separar la identidad de los pacientes y los medicamentos. 

## Solución:

Integración de tecnología blockchain en las prescripciones a fin de crear procesos eficientes en la verificación de recetas médicas y evitar las falsificaciones.

Se necesitan tres características para que las prescripciones puedan ser electrónicas: garantizar la integridad de los datos, garantizar la identidad del médico y garantizar que sólo se compre una vez. 

Blockchain permite registrar el historial de transacciones de todos los jugadores participantes en el proceso.

Cada prescripción se mandará por email al paciente, por mensaje de texto o se imprimirá la transcripción firmada electrónicamente y el paciente va con el documento impreso firmado electrónicamente a la farmacia.
Finalmente, el comercio verificará la prescripción, a través de un código QR, con un sistema que valida la matrícula profesional del médico y verifica que los datos que están guardados con tecnología blockchain sean iguales a los que se encuentran impresos.

## Contrato:

Ropsten Test Network
0x8b3605d52cd0a1688d4699ff57cd3f2be4dc988a


```sh
function addRegulatoryAuthority(address _regulatoryAuthority, string memory _name) public onlyOwner returns (bool success)

function getRegulatoryAuthorities(address _regulatoryAuthority) public view onlyOwner returns(bool success, string memory name)

function addPhysician(address _physician, uint _license, string memory _name, string memory _lastname, bytes32 _signature) public onlyRegulatoryAuthority returns (bool success)

function getPhysician(address _physician) public view returns(bool success, uint _license, string memory physicianName, string memory physicianLastname)

function addPatient(address _patient, string memory _name, string memory _lastname, string memory _affiliateNumber, uint _sex, uint _birthDay) public onlyPhysician returns (bool success)

function addPharmacist(address _pharmacist, string memory _name) public onlyRegulatoryAuthority returns (bool success)

function createPresciption(address _patient, string[] memory _drugs, string memory _diagnosis, uint _date, string memory _place) public onlyPhysician returns (bool success, int prescriptionCode)

function getPresciption(int _prescriptionCode) public onlyPhysiciansOrPatientsOrPharmacists returns (bool success, address physicianAddress, address patientAddress, string[] memory drugs, string memory diagnosis, uint date, string memory place, bytes32 signature, uint status)
```
