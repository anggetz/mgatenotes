## Doc Template Product M-GATE 

(https://documenter.getpostman.com/view/7468642/2s9YBz3vgE#ab0604f5-e6ca-4dca-9f58-42ac73ee68eb

Doc mgate

Mgate punya 3 repo,

1. repo utama berisi banya repo seperti transport, common dkk
2. Repo helmchart untuk orchestra helm chart dari repo workspace
3. Repo workspace untuk tempat kerja developer

## 1.1. Repo utama
	Berisi coding core untuk mgate, disini terdapat macam2 repo ada transport common dll kita bisa custom kalau sudah ada persetujuan dari mas willy.

### 1.1.1 Transport
	- Jika set port untuk as server wajib 4 digit jika tidka makan tidak berhasil.

## 3.1. Repo Workspace
	Di repo workspace ada 2 yml, 1 yml untuk orchestration repo helmchart, yaml kedua adalah untuk env value untuk repo helmchart (bisa diliat ada beberapa kondisi di repo helmchart menggunakan env dari repo 	workspace).

###3.1.1. Custom Repo workspace
	Developer bisa mengcustom coding di repo workspace , yang di override adalah coding yang di repo utama. Lalu skemanya bagaimana.

	1. kita perlu membuat dockerfile yang use image dari hasil build image di repo utama
	As example:

	FROM [name image from nexus repo]:[tag]
	// do customise here

 	```
  	FROM nexus.pactindo.com:8443/micro-gate/transport:3.1.8
	```
  

Di atas adalah contoh dockerfilenya, selanjutnya kita cukup build dockerfile tersebut dengan name image sama dan tag sama lalu push ke nexus repo,

Untuk deploying kita bisa manual jalankan helmchart yml yang ada di repo workspace saat ssh ke server dev or prod.


3.1.2. XML


Dalam xml semua tag akan di proses dan di validasi di bagian tag group attr filter di value ke empat jika tidak maka code akan otomatis mencari hingga match jika tidak ada yang match maka code akan membalikan error.

3.1.2.1. xml group tag

Untuk grouping processor, didalam group ada filter yang akan mapping value dengan table yang ada di databaes (m_feature_map, dan m_rest_url) 

	- Filter
	Attribute untuk penentuan tag, incoming outgoing, feature code dan validasi
	- Description
	Untuk description dari group tag.
	
3.1.2.2. processor

	- Name
	Nama share library yang akan dipakai JSONParser.so, DattaSetter.so, JSONBuilder.so

FAQ:
	Cara ubah mti dengan set field trmtio

3.1.2.2.1 Parameter
	Untuk set param value
		○ Set untuk set field dengan value
			§ Data
			Format data
				□ Static
				Jika ingin mengisi data statis
				□ Field
				Jika ingin set dengan data yang ada di field
	4. Module
	
	4.1.    ATM
		AJ, Alto, Bifast.
		
		Bifast biasanya as server and as client
		As client tidak perlu setup expose transport port
		As server perlu setup expose transport port.


	5. Database
	m_ofs:
	Info perlu coCode (as code branch bank)
	Jika digabung dengan field maka /coCode##[field]

	m_module.properties
	//change port self module
	Properties
iso.mtiMap => "0220:F,N" // means 0220 di map ke fin.req untuk read di processor
	
	const (
		Normal       = "N"
		Advice       = "A"
		Repeat       = "R"
		Notification = "NT"
	)
	
	
	Table m_transport:
	"rest.server.port"=>"17000"
	"res.server.timeout"=>number default default timeout mgate 55
	Jika type 2 (as server and as client) maka yang di pakai yang di properties
	Jika type 1 (as server) maka yang dipakai di kolom port
	Jika type 0 (as client) maka kolom port adalah destination port.
	
	Properties m_transport:
	
	# signature plugin target
	"rest.server.interceptor" => "ServerHmacSha256.so" 
	
	# signature key
	"hmacSha256.server.key" => "theKey"
	
	# signature field
	Key of header signature.
	"signature.field" => "signature"
	

	6.  Response 

	Rscp 19 = 19 system offline
	
	# BIT
	
	Bit 18 = 18 length selalu 4 dan biasanya buat temrinal type 
	6017=01 | 6014=02 | 6010=03 | *all=99
	
	# Signature
	
	
	7. Teory
	
	## Terms
	TOFS = Teller to bi fast
	CORE => to all channel or switching
	
	AH =>  Ascii Header 4 digit menentukan length
	BE => Binary Exclude 2 byte header = 100  …………n(100)
	BI => Binary Include header = 102 ……..n(100) akan ada kelebihan 2
	LF => Line Fit (new line)
	100
	299
	2123
	
	
	8. Creating Module NOTES
	
	Ketika create module pastikan monitorable is true dan node manager di restart
	
	
	9. Creating feature
		a. Socket
		○ m_feature
		○ m_feature_map
		○ Jangan lupa bit 3 2 angka depan = process code
		○ Jangan lupa bitmap.so di xml channel
		○ Jangan lupa nama field dengan tambahan angka dibelakang = mendapatkan value pada index array


	10. T24 field stored
		a. OFS.ResDesc menyimpan message error
		b. OFS.ResCount menyimpan jumlah array 
		c. OFS.Result menyimpan result dari OFS untuk parsing ke json

	11. 
	

kalau mau buat load balncer perlu nambah config helmfile seperti ini, misal contohnya module eb
-name: eb
  <<: *default
  values:
  - *val
  - transport:
      port: 30700
      loadBalancer:
        enable: true
        port: 80

1. T24 bikin jurnal, tapi statusnya masih belum dicommit (masih ngegantung)
2. T24 kirim ke iGate
3. iGate ke bifast engine
4. dst
5. kalau sukses iGate kirim response sukses ke T24
6. kalau T24 terima sukses dari iGate, baru jurnalnya dicommit



field.xxx =  value dari field
bit.xxx = value dari bit
seq =  sequence 
rspa =  action msg 
msfunc =  function class nya (N: Normal, A: Advice, R: Repeat, NT: Notification) 
msnmic = network management information code (gapernah make)

operator
"[blank]" = value kosong
"[not-blank]" = value tidak kosong
"in()" = value ada di in () (list seperate with .)
"not()" = value tidak ada di not () (list seperate with .)
"like()" =  value contain
"gt()" =  value greater than
"lt()" =  value less than
"gte()" =  value greater than equal
"lte()" =  value less than
"sw()" =  value start with
"ew() " =  value end with

 bit3 =  trtrty (2) + trtrfa (2) + trtrta (2)

Consent waktu reversal

Pastikan financial centang, untuk trigger cache hazel cast 

Bit 90 untuk reversal dibuild by
format nya gini 
0200 + origin bit 11 + origin bit 7 + origin bit 32 (left pading zero 11 digit ) + filler zero 11 digit

Jika orig key terisi maka format akan berubah



## RECONCILE SETUP

Untuk trigger mgate jalankan reconcile perlu di setup di m_reconcile_file
Mgate akan auto jalankan reconcile sesuai schedulenya

Jika ingin trigger manual jalankan dishell:
wget localhost:1208/gen-reconcile?date=2022-12-08

untuk config port recincile atau txdata
txdata:
  image:
    tag: "3.1.3"
    pullPolicy: IfNotPresent
  httpPort: "1208"
