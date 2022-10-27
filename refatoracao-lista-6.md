<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Sistema de cadastro de cliente em java - <a href="https://github.com/Geessyca/POO-List6"/>Repositório</a> 
</h4>
</br>
<h4>✔️ Todos os arquivos que ultizam algum elemento da biblioteca javax.swing foi criado a class SwingUtils para evitar duplicação de codigo</h4></br>

```
public class SwingUtils {

	public static JButton createButton (ActionListener handleClick, String labelButton, int[] size) {
		JButton button = new JButton(labelButton);
		button.setBounds(size[0], size[1],size[2], size[3]);
        button.addActionListener(handleClick);
        return button;
	}
	
	public static JLabel  createLabel (String labelScreen, int[] size) {
		JLabel screen = new JLabel();
		screen.setText(labelScreen);
		screen.setBounds(size[0], size[1],size[2], size[3]);
		return screen;
	}
	
	public static JTextArea  createTextArea (String data) {
		JTextArea textArea = new JTextArea();
		textArea.setText(data);
		textArea.setBounds(50, 100, 350, 200);
        return textArea;
	}
	
	public static JTextField  createTextField (int[] size) {
		JTextField textField = new JTextField();
		textField.setText("");
		textField.setBounds(size[0], size[1],size[2], size[3]);
        return textField;
	}

}
```

<h4>
✔️ Todos os arquivos foram renomeados para nomes relacionados as suas devidas funções </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>

</br>
<h4>Na classe Main foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Main extends JFrame{
	JButton jbtPF, jbtPJ,jbtDad;
        Vector <Cliente> meusclientes = new Vector<Cliente>();
        CadastraPJ pj = new CadastraPJ(this);
        CadastraPF pf = new CadastraPF(this);
        
	public Main(){
		getContentPane().setLayout(null);
		setTitle("Tela Principal");
		Handler obj = new Handler();
		
                
                jbtDad = new JButton("Todos Cadastros");
                jbtDad.setBounds(10,110,150,30);
                jbtDad.addActionListener(obj);
                add(jbtDad);
                
                jbtPF = new JButton("Pessoa Fisica");
                jbtPF.setBounds(10,10,150,30);
                jbtPF.addActionListener(obj);
                add(jbtPF);
                jbtPJ = new JButton("Pessoa Juridica");
                jbtPJ.setBounds(10,60,150,30);
                jbtPJ.addActionListener(obj);
                add(jbtPJ);
                setBounds(10,10,300,300);
                setVisible(true);
                setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        }
        public void cadastra(Cliente c){
            meusclientes.add(c);
        }
        public void showPrincipal(){
            pf.setVisible(false);
            pj.setVisible(false);
        }
        public void showCadastraPJ(){
            pf.setVisible(false);
            pj.setVisible(true);
        }
        public void showCadastraPF(){
            pf.setVisible(true);
            pj.setVisible(false);
        }
        public void TodosCadastros(){
            
            pf.setVisible(false);
            pj.setVisible(false);
        }
        public class Handler implements ActionListener{
            public void actionPerformed(ActionEvent e){
                if(e.getSource()==jbtPF){
                    showCadastraPF();
                }
                if(e.getSource()==jbtPJ){
                    showCadastraPF();
                }
                if(e.getSource()==jbtDad){
                   new MostraDados(meusclientes);
                }
            }
        }
        public static void main(String[] args) {
            new Main();
        }

}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Main extends JFrame{
	JButton buttonPhysicalPerson, buttonLegalPerson,buttonAllRegistration;
        Vector <Client> myCustomers = new Vector<Client>();
        RegisterLegalPerson legalPerson = new RegisterLegalPerson(this);
        RegisterPhysicalPerson physicalPerson = new RegisterPhysicalPerson(this);
        
	public Main(){
		getContentPane().setLayout(null);
		setTitle("Gerenciamento de clientes");
		Handler handleClick = new Handler();
		
				int[] buttonAllRegistrationSize  = {10,110,150,30};
                buttonAllRegistration = SwingUtils.createButton(handleClick,"Todos Cadastros", buttonAllRegistrationSize);
                add(buttonAllRegistration);
                
                int[] buttonPhysicalPersonSize  = {10,10,150,30};
                buttonPhysicalPerson = SwingUtils.createButton(handleClick,"Pessoa Fisica", buttonPhysicalPersonSize);
                add(buttonPhysicalPerson);
                
                int[] buttonLegalPersonSize  = {10,60,150,30};
                buttonLegalPerson = SwingUtils.createButton(handleClick,"Pessoa Juridica", buttonLegalPersonSize);
                add(buttonLegalPerson);


                setBounds(10,10,300,300);
                setVisible(true);
                setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        }
        public void register(Client customer){
            myCustomers.add(customer);
        }
        public void screenMain(){
            physicalPerson.setVisible(false);
            legalPerson.setVisible(false);
        }
        public void screenAllRegistration(){
            physicalPerson.setVisible(false);
            legalPerson.setVisible(false);
        }
        public class Handler implements ActionListener{
            public void actionPerformed(ActionEvent e){
                if(e.getSource()==buttonPhysicalPerson){
                	physicalPerson.setVisible(true);
                    legalPerson.setVisible(false);
                }
                if(e.getSource()==buttonLegalPerson){
                    physicalPerson.setVisible(false);
                    legalPerson.setVisible(true);
                }
                if(e.getSource()==buttonAllRegistration){
                   new ShowData(myCustomers);
                }
            }
        }
        public static void main(String[] args) {
            new Main();
        }

}
```

</br>
<h4>Na classe Client foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public abstract class Cliente {
    private long codigo;

    public Cliente(long codigo) {
        this.codigo = codigo;
    }
        public long getCodigo() {
            return codigo;
        }
        public void setCodigo(long codigo) {
            this.codigo = codigo;
        }
        public abstract String todosDados();
        
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public abstract class Client {
    private long clientCode;

    public Client(long clientCode) {
        this.clientCode = clientCode;
    }
    public long getClientCode() {
        return clientCode;
    }
    public void setClientCode(long clientCode) {
    	this.clientCode = clientCode;
    }
	public abstract String allCustomerData();
        
}
```

</br>
<h4>As sub-classes que herdaram a classe Client foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class PF extends Cliente{

    public PF(double alt,double larg) {
    	this.alt = alt;
        this.larg = larg;
    }
    public double getCpf() {
        return cpf;
    }
    
    public String todosDados(){
        return "Codigo:"+getCodigo() + " CPF:" + getCpf();
    }
}
--------------------------------------------------------------
public class PJ extends Cliente{
    private String cnpj;

    public PJ(long codigo,String cnpj) {
        super(codigo);
        this.cnpj = cnpj;
    }

    public String getCnpj() {
        return cnpj;
    }
    public void setCnpj(String cnpj) {
        this.cnpj = cnpj;
    }
    public String todosDados(){
        return "Codigo:"+getCodigo() + "CNPJ" + getCnpj();
   
}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class PhysicalPerson extends Client{
	private String cpf;

	public PhysicalPerson(long codigo,String cpf) {
		 super(codigo);
	     this.cpf = cpf;
    }
	public String getCpf() {
		return cpf;
	}
	public void setCpf(String cpf) {
		this.cpf = cpf;
	}
    public String todosDados(){
        return "Codigo:"+getClientCode() + " CPF:" + getCpf();
    }
}
--------------------------------------------------------------
public  class LegalPerson extends Client{
    private String cnpj;

    public LegalPerson(long codigo,String cnpj) {
        super(codigo);
        this.cnpj = cnpj;
    }

    public String getCnpj() {
        return cnpj;
    }
    public void setCnpj(String cnpj) {
        this.cnpj = cnpj;
    }
    public String todosDados(){
        return "Codigo:"+getClientCode() + "CNPJ" + getCnpj();
   
    }
}
```

</br>
<h4>Na classe de registro de pessoa fisica foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class CadastraPF extends JDialog{
    JButton jbtCad,jbtCan;
    JTextField jtfCodigo, jtfCpf;
    JLabel jlCodigo, jlCpf;
    Main pc;
    Handler obj = new Handler();
    public CadastraPF(Main pc){
        this.pc = pc;
        getContentPane().setLayout(null);
		setTitle("Tela PF");
                
                //Butoes
                jbtCad = new JButton("Cadastrar");
                jbtCad.setBounds(10,10,150,30);
                jbtCad.addActionListener(obj);
                add(jbtCad);
                jbtCan = new JButton("Cancelar");
                jbtCan.setBounds(10,60,150,30);
                jbtCan.addActionListener(obj);
                add(jbtCan);
                
                //TextField
                jtfCpf = new JTextField(); 
                jtfCpf.setText("");
                jtfCpf.setBounds(25,125,150,30);
                add(jtfCpf);
                jtfCodigo = new JTextField(); 
                jtfCodigo.setText("");
                jtfCodigo.setBounds(25,200,150,30);
                add(jtfCodigo);
                
                //TextLabel
                jlCpf = new JLabel(); 
                jlCpf.setText("CPF:");
                jlCpf.setBounds(25,100,150,30);
                add(jlCpf);
                jlCodigo = new JLabel(); 
                jlCodigo.setText("Codigo:");
                jlCodigo.setBounds(25,175,150,30);
                add(jlCodigo);
                
                setBounds(10,10,300,300);
    }
    public class Handler implements ActionListener{
            public void actionPerformed(ActionEvent e){
                if(e.getSource()== jbtCan){
                    pc.showPrincipal();
                }
                if(e.getSource()== jbtCad){
                    PF aux =  new PF(Long.parseLong(jtfCodigo.getText()),jtfCpf.getText());
                    pc.cadastra(aux);
                    jtfCodigo.setText("");
                    jtfCpf.setText("");
                }
            }
        }
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class RegisterPhysicalPerson extends JDialog{
    JButton buttonRegistration,buttonToBack;
    JTextField fieldCode, fieldCpf;
    JLabel labelCode, labelCpf;
    Main main;
    Handler handleClick = new Handler();
    public RegisterPhysicalPerson(Main main){
        this.main = main;
        getContentPane().setLayout(null);

		setTitle("Registrar pessoa fisica");    
			int[] buttonRegistrationSize  = {10,10,150,30};
			buttonRegistration = SwingUtils.createButton(handleClick,"Cadastrar", buttonRegistrationSize);
	        add(buttonRegistration);
	        
	        int[] buttonToBackSize  = {10,60,150,30};
	        buttonToBack = SwingUtils.createButton(handleClick,"Voltar", buttonToBackSize);
	        add(buttonToBack);

	        int[] fieldCpfSize  = {25,125,150,30};
	        fieldCpf = SwingUtils.createTextField(fieldCpfSize);
	        add(fieldCpf);

	        int[] fieldCodeSize  = {25,200,150,30};
	        fieldCode = SwingUtils.createTextField(fieldCodeSize);
	        add(fieldCode);
	        
	        int[] labelCpfSize  = {25,100,150,30};
	        labelCpf = SwingUtils.createLabel("CPF:",labelCpfSize);
	        add(labelCpf);

	        
	        int[] labelCodeSize  = {25,175,150,30};
	        labelCode = SwingUtils.createLabel("Codigo:",labelCodeSize);
	        add(labelCode);
	        
            setBounds(10,10,300,300);
    }
    public class Handler implements ActionListener{
            public void actionPerformed(ActionEvent e){
                if(e.getSource()== buttonToBack){
                    main.screenMain();
                }
                if(e.getSource()== buttonRegistration){
                    PhysicalPerson aux =  new PhysicalPerson(Long.parseLong(fieldCode.getText()),fieldCpf.getText());
                    main.register(aux);
                    fieldCode.setText("");
                    fieldCpf.setText("");
                }
            }
        }
}
```

</br>
<h4>Na classe de registro de pessoa juridica foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class CadastraPJ extends JDialog{
    JButton jbtCad,jbtCan;
    JTextField jtfCodigo, jtfCnpj;
    JLabel jlCodigo, jlCnpj;
    Main pc;
    Handler obj = new Handler();
    public CadastraPJ(Main pc){
        this.pc = pc;
        getContentPane().setLayout(null);
		setTitle("Tela PJ");
                //Butoes
                jbtCad = new JButton("Cadastrar");
                jbtCad.setBounds(10,10,150,30);
                jbtCad.addActionListener(obj);
                add(jbtCad);
                jbtCan = new JButton("Cancelar");
                jbtCan.setBounds(10,60,150,30);
                jbtCan.addActionListener(obj);
                add(jbtCan);
                
                //TextField
                jtfCnpj = new JTextField(); 
                jtfCnpj.setText("");
                jtfCnpj.setBounds(25,125,150,30);
                add(jtfCnpj);
                jtfCodigo = new JTextField(); 
                jtfCodigo.setText("");
                jtfCodigo.setBounds(25,200,150,30);
                add(jtfCodigo);
                
                //TextLabel
                jlCnpj = new JLabel(); 
                jlCnpj.setText("CNPJ:");
                jlCnpj.setBounds(25,100,150,30);
                add(jlCnpj);
                jlCodigo = new JLabel(); 
                jlCodigo.setText("Codigo:");
                jlCodigo.setBounds(25,175,150,30);
                add(jlCodigo);
                
                setBounds(10,10,300,300);
    }
    public class Handler implements ActionListener{
            public void actionPerformed(ActionEvent e){
                if(e.getSource()== jbtCan){
                    pc.showPrincipal();
                }
                if(e.getSource()== jbtCad){
                    PJ aux =  new PJ(Long.parseLong(jtfCodigo.getText()),jtfCnpj.getText());
                    pc.cadastra(aux);
                    jtfCodigo.setText("");
                    jtfCnpj.setText("");
                }
            }
        }
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class RegisterLegalPerson extends JDialog{
    JButton buttonRegistration,buttonToBack;
    JTextField fieldCode, fieldCnpj;
    JLabel labelCode, labelCnpj;
    Main main;
    Handler handleClick = new Handler();
    public RegisterLegalPerson(Main main){
        this.main = main;
        getContentPane().setLayout(null);
		setTitle("Registrar pessoa juridica");
		int[] buttonRegistrationSize  = {10,10,150,30};
		buttonRegistration = SwingUtils.createButton(handleClick,"Cadastrar", buttonRegistrationSize);
        add(buttonRegistration);
        
        int[] buttonToBackSize  = {10,60,150,30};
        buttonToBack = SwingUtils.createButton(handleClick,"Voltar", buttonToBackSize);
        add(buttonToBack);

        int[] fieldCnpjSize  = {25,125,150,30};
        fieldCnpj = SwingUtils.createTextField(fieldCnpjSize);
        add(fieldCnpj);

        int[] fieldCodeSize  = {25,200,150,30};
        fieldCode = SwingUtils.createTextField(fieldCodeSize);
        add(fieldCode);
        
        int[] labelCnpjSize  = {25,100,150,30};
        labelCnpj = SwingUtils.createLabel("CNPJ:",labelCnpjSize);
        add(labelCnpj);

        
        int[] labelCodeSize  = {25,175,150,30};
        labelCode = SwingUtils.createLabel("Codigo:",labelCodeSize);
        add(labelCode);
                
                setBounds(10,10,300,300);
    }
    public class Handler implements ActionListener{
            public void actionPerformed(ActionEvent e){
                if(e.getSource()== buttonToBack){
                    main.screenMain();
                }
                if(e.getSource()== buttonRegistration){
                    LegalPerson aux =  new LegalPerson(Long.parseLong(fieldCode.getText()),fieldCnpj.getText());
                    main.register(aux);
                    fieldCode.setText("");
                    fieldCnpj.setText("");
                }
            }
        }
}
```

</br>
<h4>Na classe de exibição dos dados foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class MostraDados extends JDialog{
        JButton jbtFechar;
	JTextArea jtaTDados;
	Vector<Cliente> clientes;
	public MostraDados(Vector<Cliente> c) {
		clientes = c;
		getContentPane().setLayout(null);
		setTitle("Dados Gerais");
		Handler obj = new Handler(); 
		jbtFechar = new JButton("Voltar");
		jbtFechar.setBounds(10, 10, 100, 40);
		jbtFechar.addActionListener(obj);
		add(jbtFechar);
		jtaTDados = new JTextArea();
		jtaTDados.setBounds(50, 100, 350, 200);
		jtaTDados.setText(dadosFormatados());
		add(jtaTDados);
		setBounds(120,120,450,450);
		setVisible(true);
		setModal(true);
	}

	public String dadosFormatados() {
		String m = "";
		for(int i=0;i<clientes.size();i++) {
			m = m + "\n" + clientes.get(i).todosDados();
		}
		return m;
	}
	public class Handler implements ActionListener{
		public void actionPerformed(ActionEvent e){
			if(e.getSource() == jbtFechar) {

				setVisible(false);
			}
		}
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class ShowData extends JDialog{
        JButton buttonToBack;
	JTextArea textArea;
	Vector<Client> client;
	public ShowData(Vector<Client> clients) {
		client = clients;
		getContentPane().setLayout(null);
		setTitle("Dados dos clientes");
		Handler handleClick = new Handler(); 
		 
        int[] buttonToBackSize  = {10, 10, 100, 40};
        buttonToBack = SwingUtils.createButton(handleClick,"Voltar", buttonToBackSize);
        add(buttonToBack);


        textArea = SwingUtils.createTextArea(formattedData());
        add(textArea);
       
		setBounds(120,120,450,450);
		setVisible(true);
		setModal(true);
	}

	public String formattedData() {
		String message = "";
		for(int i=0;i<client.size();i++) {
			message = message + "\n" + client.get(i).getClientCode();
		}
		return message;
	}
	public class Handler implements ActionListener{
		public void actionPerformed(ActionEvent e){
			if(e.getSource() == buttonToBack) {
				setVisible(false);
			}
		}
	}
}
```
