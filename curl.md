/qr-code
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/qr-code");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);

	$response = curl_exec($client);

    $info = curl_getinfo($client);	
    
    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);   

Response

{"value":"1@45HCl6uZDyNQyEtV7VyWkzS82bDlJfa2OP2gmhuoIM8+Yxu8nJ/,msrACb/MhBC8ssvdPu0T3deCCNX1hfDLo+N/Ot6Uw=,GhThpswKhatgLgHFs0jw=="}

Observação

- Falta tratamentos de erro ou documentar se existe;
- Está retornando o status 200 mas quando ocorre um erro do tipo passar o id de sessão errado retorna status 500 não retornou um erro dizendo que o id de sessão estava incorreto
mas sim status 500 Internal Server Error.  




/qr-code/image

<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/qr-code/image");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);   

Response

{"value":"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQgAAAEIAQMAAACZOPi..."}

Observação

- Falta tratamentos de erro ou documentar se existe;
- Está retornando o status 200 mas quando ocorre um erro do tipo passar o id de sessão errado retorna status 500 não retornou um erro dizendo que o id de sessão estava incorreto
mas sim status 500 Internal Server Error.  




/restart
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/restart");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
	curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);

	$response = curl_exec($client);
     
    $info = curl_getinfo($client); 

    if ($info["http_code"] == 200) { 
		$response = json_encode(array("status" => $info["http_code"], "info" => "success"));
    } else {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);  

Response

Está retornando apenas o status.

Observação

- Falta tratamentos de erro ou documentar se existe;
- Não possui um retorno dizendo que está certo apenas o status, na documentação informa que o status de sucesso é 200 mas está retornando 204




/disconnect
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/disconnect");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);   

Response

{"message":"Desconectado com sucesso!"}

Observação

- Falta tratamentos de erro ou documentar se existe.




/status
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/status");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);    

Response

Não Conectado!
{"connected":false,"error":"You are not connected.","created":1590797022000}

Conectado!
{"connected":true,"error":"You are already connected.","created":1590797072000}

Observação

- Falta tratamentos de erro ou documentar se existe.




/send-text
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-text");

    $data = array("phone" => "5544999999999", "message" => "Hello World");

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );       

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"3884378F820F90FE923E0242AC110002"}

Observação

- Falta tratamentos de erro ou documentar se existe.




/send-contact
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-contact");

    $data = array(
    	"phone" => "5544999999999", 
		"contactName" => "Rogerio Aldair",
		"contactPhone" => "5544999999999",
		"contactBusinessDeion" => "Fale com nossos atendentes."
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"38843861BBF660FB03F30242AC110002"}

Observação

- Falta tratamentos de erro ou documentar se existe.    




/send-image
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-image");

    $data = array(
    	"phone" => "5544999999999", 
		"image" => "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAYABgAAD/4QAiRXhpZ..."
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"388444CB6E69105FC6670242AC110002"}

Observação

- Falta tratamentos de erro ou documentar se existe.    




/send-audio
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-audio");

    $data = array(
    	"phone" => "5544999999999", 
		"audio" => "data:audio/mp3;base64,SUQzBAAAAAAAI1RTU0UAAAAPAAADTGF2ZjU4LjI5Lj..."
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"38844535D38060AD6D060242AC110002"}

Observação

- Falta tratamentos de erro ou documentar se existe.  




/send-video
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-video");

    $data = array(
    	"phone" => "5544999999999", 
		"video" => "data:video/mp4;base64,AAAAIGZ0eXBpc29tAAACAGlzb21pc28yYXZjMW1wNDEAAA..."
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);   

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"3884459CCC20B0B8CB020242AC110002"}

Observação

- Falta tratamentos de erro ou documentar se existe. 




/send-document
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-document/pdf");

    $data = array(
    	"phone" => "5544999999999", 
		"document" => "data:application/pdf;base64,JVBERi0xLjcKCjQgMCBvYmoKKElkZW50aXR5KQplb..."
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"388445F9C0D1D0539A6D0242AC110002"}

Observação

- O código de retorno está como 200 quando da certo e não como 202 no Swagger;
- Por algum motivo o nome do arquivo ficou "Sem Nome.pdf"





/send-link
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-link");

    $data = array(
    	"phone" => "5544999999999", 
		"message" => "Hello World",
		"image" => "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAYABgAAD/4QAiRXhpZgAATU0AKgAAA...",
		"linkUrl" => "http://www.grands.com.br",
		"title" => "Roupas e Acessórios",
		"linkDeion" => "Integração com o whatsapp"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);    

Response

{"zaapId":"38844661B510308D373E0242AC110002"}

Observação

- Não funciona, está enviando para o celular apenas a mensagem 'Hello World' e o resto não envia    




/read-message
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/read-message");

    $data = array(
    	"phone" => "5544999999999", 
		"messageId" => "388369E8E9D50089742F0242AC110002"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    } else {
        $response = json_encode(array("status" => $info["http_code"], "info" => "success"));
    }  

    curl_close($client);

    print_r($response);    

Response

Retorna apenas o status, talvez retornar também um sucesso, não sei.

Observação

- Não tem documentação de possíveis erros.




/send-text-status
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-text-status");

    $data = array(
		"message" => "My Text Status"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);   

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);

Response

{"zaapId":"388446EA94E3809F364E0242AC110002"}

Observação

- Não tem documentação de possíveis erros.




/send-image-status
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/send-image-status");

    $data = array(
		"image" => "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAYABgAAD/4RDgRXhpZgAATU0AKgAAAAgABAE7AAIAAAAHAA...",
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);    

Response

{"zaapId":"3884473DBCE21069C9000242AC110002"}

Observação

- Não tem documentação de possíveis erros.




/chats
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/chats?page=1&pageSize=50");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3); 

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);   


Response

{"status":0,"error":"Operation timed out after 3000 milliseconds with 0 bytes received"} 


{"name":"Maria Empresa","phone":"554499999999","unread":"0","lastMessageTime":"1578940389","isMuted":"0","isMarkedSpam":"false","profileThumbnail":"https://pps.whatsapp.net/v/t61.24694-24/ID_IMAGE.jpg?oe=8888888888&oh=99999999999999999999999999999999"}]




/chat-messages
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/chat-messages/5544999999999?aumont=5");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);     

Response

{"status":0,"error":"Operation timed out after 3000 milliseconds with 0 bytes received"} 

[{"phone":"55449999999","momment":1590802987000,"messageId":"E068CD9aD841CFBs31E6","referenceMessageId":"","image":{"imageUrl":"https://storage.z-api.io/instances/MINHA_INSTANCE/ID_IMAGE.jpeg","mimeType":"image/jpeg","thumbnailUrl":"https://storage.z-api.io/instances/MINHA_INSTANCE/ID_IMAGE.jpeg"},"status":"READ"}]




/contacts
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/contacts?page=1&pageSize=50");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);     

Response

[{"phone":"554899999999"},{"phone":"55119999999"},{"phone":"55549999999"}]





/profile-picture
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/profile-picture?phone=5544999999999");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response);

Response

{"link":null}

Observação 

Não sei como é esse profile ou de onde pega        





/phone-exists
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/phone-exists/5544999999999");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($client, CURLOPT_TIMEOUT, 3);  

	$response = curl_exec($client);
    
    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client); 

    print_r($response); 

Response

{"exists":true}

Observação

- Não tem documentação de possíveis erros.





/create-group
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/create-group");

    $data = array(
		"groupName" => "Grupo Z-API",
		"phones" => [
			"5544999999999"
		]
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);    

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);  

Observação

Código de status na documentação está 202 mas está retornando 200
Não está claro o group id para eventuais alterações, no lugar do phone no retorno colocar groupId         




/update-group-name
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/update-group-name");

    $data = array(
		"groupName" => "Grupo Z-API Elite",
		"groupId" => "5544999999999-1590713331"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);       

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);   

Response

Sem retorno apenas status





/add-admin
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/add-admin");

    $data = array(
		"groupId" => "5544999999999-1590713331",
		"phones" => [
			"5544999999999"
		]
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);    

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {  	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);      

Response

Sem retorno apenas status




/remove-admin
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/remove-admin");

    $data = array(
		"groupId" => "5544999999999-1590713331",
		"phones" => [
			"5544999999999"
		]
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);    

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {   	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);       

Response

Sem retorno apenas status




/add-participant
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/add-participant");

    $data = array(
		"groupId" => "5544999999999-1590713331",
		"phones" => [
			"5544999999999"
		]
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);     

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);   

Response

Sem retorno apenas status




/remove-participant
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/remove-participant");

    $data = array(
		"groupId" => "5544999999999-1590713331",
		"phones" => [
			"5544999999999"
		]
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);     

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);  

Response

Sem retorno apenas status


/leave-group
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/leave-group");

    $data = array(
		"groupId" => "554491146917-1590713331"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'POST');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);     

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 202) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response); 

Observação

- Sem retornos apenas status    





/queue
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/queue");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'GET');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);  
    curl_setopt($client, CURLOPT_TIMEOUT, 3); 

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 200) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response); 

Response

{"size":0,"messages":[]}

Observação

Na documentação está como 204 o status mas está retornando sempre 200



/queue
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/queue");

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'DELETE');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);  
    curl_setopt($client, CURLOPT_TIMEOUT, 3); 

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 204) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response); 

Response

Retornando status 204
Não foi possível determinar se está correto          





/update-webhook-delivery
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/update-webhook-delivery");

    $data = array(
		"value" => "WEBHOOK"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'PUT');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers); 
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);    

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 204) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);     

Response

Apenas status 204




/update-webhook-disconnected
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/update-webhook-disconnected");

    $data = array(
		"value" => "WEBHOOK"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'PUT');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);   

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 204) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);     

Response

Apenas status 204




/update-webhook-received
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/update-webhook-received");

    $data = array(
		"value" => "WEBHOOK"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'PUT');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);   

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 204) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response);      

Response

Apenas status 204




/update-webhook-message-status
<?php

	$client = curl_init("https://api.z-api.io/instances/MINHA_INSTANCE/token/MEU_TOKEN/update-webhook-message-status");

    $data = array(
		"value" => "WEBHOOK"
	);

    $data_string = json_encode($data);

	$headers = array(
        "Content-Type: application/json",
        "Content-Length: " . strlen($data_string)
    );    

	curl_setopt($client, CURLOPT_CUSTOMREQUEST, 'PUT');
	curl_setopt($client, CURLOPT_RETURNTRANSFER, true);
	curl_setopt($client, CURLOPT_POSTFIELDS, $data_string);
	curl_setopt($client, CURLOPT_HTTPHEADER, $headers);  
	curl_setopt($client, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($client, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($client, CURLOPT_TIMEOUT, 3);    

	$response = curl_exec($client);

    $info = curl_getinfo($client);

    if ($info["http_code"] != 204) {	
    	$response = json_encode(array("status" => $info["http_code"], "error" => curl_error($client)));
    }   

    curl_close($client);

    print_r($response); 

Response

Apenas status 204