package fucoesSelenium;

import java.awt.AWTException;
import java.awt.Robot;
import java.awt.Toolkit;
import java.awt.datatransfer.StringSelection;
import java.awt.event.KeyEvent;
import java.io.File;
import java.util.ArrayList;
import java.util.Random;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;

public class FuncoesSelenium {

	WebElement elemento;

	String caminhoDoDriver = "C:\\Users\\henrique.garcia\\Desktop\\HENRIQUE\\HENRIQUE\\AUTOMACAO\\Drivers\\ChromeDriver\\";
	String chromeDriver = "chromedriver.exe";
	// xxxxxxxxxxxxxxxxxxxxxxxxx CLICAR EM BOTAO
	// XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

	public void iDclicaBotao(String idBotao, WebDriver driver) {

		elemento = driver.findElement(By.id(idBotao));
		esperarDoisMinutos(driver);
		elemento.click();
		esperarDoisMinutos(driver);

	}

	public void xPathclicaBotao(String xpathBotao, WebDriver driver) {
		esperarDoisMinutos(driver);
		elemento = driver.findElement(By.xpath(xpathBotao));
		driver.manage().timeouts().implicitlyWait(05, TimeUnit.SECONDS);
		elemento.click();
		esperarDoisMinutos(driver);

	}

	// xxxxxxxxxxxxxxxxxxxxxxxxx PREENCHER CAMPO
	// XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

	public void idPreencherCampo(WebDriver driver, String idDoCampo, String valorAserPreenchido) {

		WebElement elemento = driver.findElement(By.id(idDoCampo));
		esperarDoisMinutos(driver);
		elemento.click();

		esperarDoisMinutos(driver);
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		elemento.sendKeys(valorAserPreenchido);

	}

	public void idPreencherCampoJavaScript(WebDriver driver, String idDoCampo, String valorAserPreenchido) {

		esperarDoisMinutos(driver);
		clicaBotaoJavaScript(driver, idDoCampo);
		esperarDoisMinutos(driver);
		elemento.sendKeys(valorAserPreenchido);

	}

	public void idPreencherCampoComJava(WebDriver driver, String idDoCampo, String valorAserPreenchido) {

		// WebElement elemento = driver.findElement(By.id(idDoCampo));
		esperarDoisMinutos(driver);
		clicaBotaoJavaScript(driver, idDoCampo);
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		elemento = driver.findElement(By.id(idDoCampo));
		esperarDoisMinutos(driver);
		elemento.sendKeys(valorAserPreenchido);
		esperarDoisMinutos(driver);
		clicaBotaoJavaScript(driver, idDoCampo);

	}
	
	public void xpathPreencherCampoComJava(WebDriver driver, String xpathDoCampo, String valorAserPreenchido) {

		// WebElement elemento = driver.findElement(By.id(idDoCampo));
		esperarDoisMinutos(driver);
		clicaBotaoJavaScript(driver, xpathDoCampo);
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		elemento = driver.findElement(By.xpath(xpathDoCampo));
		esperarDoisMinutos(driver);
		elemento.sendKeys(valorAserPreenchido);
		esperarDoisMinutos(driver);
		clicaBotaoJavaScript(driver, xpathDoCampo);
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}


	}

	public void xpathPreencherCampo(WebDriver driver, String xpathDoCampo, String valorAserPreenchido) {

		WebElement elemento = driver.findElement(By.xpath(xpathDoCampo));
		driver.manage().timeouts().implicitlyWait(05, TimeUnit.SECONDS);
		elemento.click();
		elemento.click();
		elemento.sendKeys(valorAserPreenchido);

	}

	// xxxxxxxxxxxxxxxxxxxxxxxxx VALIDA TEXTO NA
	// TELAXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

	public boolean retornaTextoDaTelaAtual(WebDriver driver, String textoProcurado) {

		driver.findElement(By.tagName(""));

		return true;
	}

	// xxxxxxxxxxxxxxxxxxxxxxxxx ESPERAR
	// XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

	public void IDesperarElementoDaProximaTela(String idCaminhoDoCampo, WebDriver driver) {

		WebDriverWait wait = new WebDriverWait(driver, 120);
		wait.until(ExpectedConditions.visibilityOfElementLocated(By.id(idCaminhoDoCampo)));

	}

	public boolean xpathEsperarElementoDaProximaTela(String xpathDoCampo, WebDriver driver) {

		WebDriverWait wait = new WebDriverWait(driver, 60);
		wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath(xpathDoCampo)));
		esperarDoisMinutos(driver);
		return true;

	}

	public void xpathEsperarElementoDaProximaTelaSerClicavel(String xpathDoCampo, WebDriver driver) {

		WebDriverWait wait = new WebDriverWait(driver, 60);
		wait.until(ExpectedConditions.elementToBeClickable(By.id(xpathDoCampo)));
		esperarDoisMinutos(driver);

	}

	public void idEsperarElementoDaProximaTelaSerClicavel(String xpathDoCampo, WebDriver driver) {

		WebDriverWait wait = new WebDriverWait(driver, 60);
		wait.until(ExpectedConditions.elementToBeClickable(By.id(xpathDoCampo)));
		esperarDoisMinutos(driver);

	}

	public void esperarDoisMinutos(WebDriver driver) {

		driver.manage().timeouts().implicitlyWait(300, TimeUnit.SECONDS);

	}

	// xxxxxxxxxxxxxxxxxxxxxxxxx IR PARA PAGINA CORRENTE
	// XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

	public boolean irParaPaginaemFoco(WebDriver driver) {

		esperarDoisMinutos(driver);
		String nomeJanela_1 = driver.getWindowHandle();
		System.out.println("NOME DA GANELA AQUI__" + nomeJanela_1);
		driver.switchTo().window(nomeJanela_1);
		esperarDoisMinutos(driver);

		return true;

	}

	public void xpathSelecionarIndexCombobox(WebDriver driver, String xpathCombobox, int numeroIdex) {
		WebDriverWait wait = inicializa_webdriver_wait(driver);
		wait.until(ExpectedConditions.elementToBeClickable(By.xpath(xpathCombobox)));

		Select dropdown = new Select(driver.findElement(By.xpath(xpathCombobox)));
		esperarDoisMinutos(driver);
		dropdown.selectByIndex(numeroIdex);
		esperarDoisMinutos(driver);
	}

	public void idSelecionarIndexCombobox(WebDriver driver, String idCombobox, int numeroIdex) {
		WebDriverWait wait = inicializa_webdriver_wait(driver);
		wait.until(ExpectedConditions.elementToBeClickable(By.id(idCombobox)));

		Select dropdown = new Select(driver.findElement(By.id(idCombobox)));
		esperarDoisMinutos(driver);
		dropdown.selectByIndex(numeroIdex);
		esperarDoisMinutos(driver);
	}

	public boolean pesquisaDropDown(WebDriver driver, String xpathMenuDropDow, String xpath_Opcao_MenuDropDown) {

		WebElement menuSelect = driver.findElement(By.xpath(xpathMenuDropDow));
		menuSelect.click();
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		WebElement menuOpcaoescolhida = driver.findElement(By.xpath(xpath_Opcao_MenuDropDown));
		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		esperarDoisMinutos(driver);
		menuOpcaoescolhida.click();
		esperarDoisMinutos(driver);

		return true;

	}

	public boolean validarTextoDaTela(WebDriver driver, String valorAserEncontradoNaTela) {

		String textoDaTela = driver.getPageSource();

		if (textoDaTela.contains(valorAserEncontradoNaTela)) {
			System.out.println("TEXTO ENCONTRADO COM SUCESSO");
			return true;
		} else {

			System.out.println("TEXTO NÃO NÃO FOI ENCONTRADO");
			return false;

		}

	}

	public Integer criaNumerosAleatorios(int quantidade) {
		Random gerador = new Random();
		int NumeroGerado = 0;
		for (int i = 0; i < quantidade; i++) {

			NumeroGerado = gerador.nextInt();

		}
		return NumeroGerado;
	}

	public boolean clicaBotaoJavaScript(WebDriver driver, String xpathBotao) {
		WebElement elemento = driver.findElement(By.xpath(xpathBotao));

		JavascriptExecutor js = (JavascriptExecutor) driver;
		esperarDoisMinutos(driver);
		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		js.executeScript("arguments[0].click();", elemento);
		esperarDoisMinutos(driver);
		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return true;

	}

	// xxxxxxxxxxxxxxxxxxxxxxxxx TABELAS
	// XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

	public boolean xpathValidaTextoDaGrid(WebDriver driver, String textoASerValidadoNaGrid, String xpathDaTabela) {
		// DECLARA ARRAYLIST
		ArrayList<String> listaDeLinhasDaGrid = new ArrayList<String>();
		WebElement elemento;

		// CONTA QUANTAS LINHAS A GRID POSSUI
		int Row_count = driver.findElements(By.xpath(xpathDaTabela)).size();
		System.out.println("QUANTIDADE MAXIMA DE LINHAS NA TABELA__" + Row_count);

		// PERCORRE TODA A TABELA

		for (int i = 1; i < Row_count; i++) {

			elemento = driver.findElement(
					By.xpath("//*[@id=\"content-page\"]/div/section/div/div/div[3]/table[2]/tbody/tr[" + i + "1]"));
			listaDeLinhasDaGrid.add(elemento.toString());

			for (String linha : listaDeLinhasDaGrid) {

				if (linha.contains(textoASerValidadoNaGrid)) {

					System.out.println("TEXTO ENCONTRADO NA TABELA");
					return true;

				}

			}

		}
		return false;

	}

	public String getPageSource(WebDriver driver) {
		String textoDaPaginaToda = driver.getPageSource();
		return textoDaPaginaToda;
	}

	public WebDriverWait inicializa_webdriver_wait(WebDriver driver) {

		WebDriverWait wdw = new WebDriverWait(driver, 40);

		return wdw;

	}

	public String funcaoCaminhoDoWebDriverBrowser(String caminhoDoDriver, String nomeDoBrowserdriver) {
		String chromeDriver = caminhoDoDriver + nomeDoBrowserdriver;
		return chromeDriver;

	}

	public WebDriver utilizarChromeDriverAbaAnonima() {
		String caminhoDoDriver = funcaoCaminhoDoWebDriverBrowser(getCaminhoDoWebDriver(), getChromeDriver());

		System.setProperty("webdriver.chrome.driver", caminhoDoDriver);

		// DRIVER
		WebDriver driver = new ChromeDriver();
		ChromeOptions options = new ChromeOptions();
		options.addArguments("--incognito");
		driver = new ChromeDriver(options);

		return driver;
	}

	public WebDriver utilizarChromeDriver() {
		String caminhoDoDriver = funcaoCaminhoDoWebDriverBrowser(getCaminhoDoWebDriver(), getChromeDriver());

		System.setProperty("webdriver.chrome.driver", caminhoDoDriver);

		// DRIVER
		WebDriver driver = new ChromeDriver();
		ChromeOptions options = new ChromeOptions();
		options.addArguments("--start-maximized");
		driver = new ChromeDriver(options);

		return driver;
	}

	public String getCaminhoDoWebDriver() {

		return this.caminhoDoDriver;
	}

	public String getChromeDriver() {

		return this.chromeDriver;
	}

	public boolean uploadDeArquivo(WebDriver driver, String xpathDoBotaoDeUpload, String caminhoDoArquivo)
			throws AWTException {

		 WebElement elemento = driver.findElement(By.xpath(xpathDoBotaoDeUpload));
		clicaBotaoJavaScript(driver, xpathDoBotaoDeUpload);
		elemento.click();
		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

		StringSelection ss = new StringSelection(caminhoDoArquivo);

		Toolkit.getDefaultToolkit().getSystemClipboard().setContents(ss, null);

		Robot robot = new Robot();

		robot.keyPress(KeyEvent.VK_CONTROL);
		robot.keyPress(KeyEvent.VK_V);
		robot.keyRelease(KeyEvent.VK_V);
		robot.keyRelease(KeyEvent.VK_CONTROL);
		robot.keyPress(KeyEvent.VK_ENTER);
		robot.keyRelease(KeyEvent.VK_ENTER);

		esperarDoisMinutos(driver);

		return true;
	}

	public String pegaNomeDoArquivo(String caminhoDoArquivo) {

		File file = new File(caminhoDoArquivo);
		String nomeDoArquivo = file.getName();
		return nomeDoArquivo;
	}

	public WebDriver browserAbaAnonimaChrome() {

		DesiredCapabilities capabilities = DesiredCapabilities.chrome();
		ChromeOptions options = new ChromeOptions();
		options.addArguments("--incognito");
		capabilities.setCapability(ChromeOptions.CAPABILITY, options);
		System.setProperty("webdriver.chrome.driver", caminhoDoDriver);
		@SuppressWarnings("deprecation")
		WebDriver driver = new ChromeDriver(capabilities);
		esperarDoisMinutos(driver);
		return driver;
	}

}

