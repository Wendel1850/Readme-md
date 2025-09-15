recicla365/
public/
index.html
src/
components/
CadastroLocal.js
Dashboard.js
ListagemLocais.js
Login.js
Menu.js
containers/
App.js
index.js
styles/
global.css
utils/
api.js
App.css
App.test.js
index.js
package.json
README.md

import React, { useState } from 'react';

function Login() {
  const [email, setEmail] = useState('');
  const [senha, setSenha] = useState('');

  const handleSubmit = (event) => {
    event.preventDefault();
    // Lógica de autenticação aqui
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="email" value={email} onChange={(e) => setEmail(e.target.value)} />
      <input type="password" value={senha} onChange={(e) => setSenha(e.target.value)} />
      <button type="submit">Entrar</button>
    </form>
  );
}

export default Login;

import React, { useState } from 'react';

function CadastroLocal() {
  const [nome, setNome] = useState('');
  const [descricao, setDescricao] = useState('');
  const [cep, setCep] = useState('');
  const [logradouro, setLogradouro] = useState('');
  const [bairro, setBairro] = useState('');
  const [cidade, setCidade] = useState('');
  const [estado, setEstado] = useState('');
  const [numero, setNumero] = useState('');

  const handleSubmit = (event) => {
    event.preventDefault();
    // Lógica de cadastro de local de coleta aqui
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={nome} onChange={(e) => setNome(e.target.value)} />
      <input type="text" value={descricao} onChange={(e) => setDescricao(e.target.value)} />
      <input type="text" value={cep} onChange={(e) => setCep(e.target.value)} />
      <input type="text" value={logradouro} readOnly />
      <input type="text" value={bairro} readOnly />
      <input type="text" value={cidade} readOnly />
      <input type="text" value={estado} readOnly />
      <input type="text" value={numero} onChange={(e) => setNumero(e.target.value)} />
      <button type="submit">Cadastrar</button>
    </form>
  );
}

export default CadastroLocal;
.login-container {
  max-width: 400px;
  margin: 40px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.login-form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.login-form input[type="email"],
.login-form input[type="password"] {
  width: 100%;
  height: 40px;
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.login-form button[type="submit"] {
  width: 100%;
  height: 40px;
  background-color: #4CAF50;
  color: #fff;
  padding: 10px;
  border: none;
  import React, { useState, useEffect } from 'react';
import axios from 'axios';

const Endereco = ({ cep }) => {
  const [endereco, setEndereco] = useState({});

  useEffect(() => {
    axios.get(`https://viacep.com.br/ws/${cep}/json/`)
      .then(response => {
        setEndereco(response.data);
      })
      .catch(error => {
        console.error(error);
      });
  }, [cep]);

  return (
    <div>
      <p>Logradouro: {endereco.logradouro}</p>
      <p>Bairro: {endereco.bairro}</p>
      <p>Cidade: {endereco.localidade}</p>
      <p>Estado: {endereco.uf}</p>
    </div>
  );
};

export default Endereco;
const cep = '01001000';

fetch(`https://viacep.com.br/ws/${cep}/json/`)
  .then(response => response.json())
  .then(data => {
    console.log(data);
    const endereco = {
      logradouro: data.logradouro,
      bairro: data.bairro,
      cidade: data.localidade,
      estado: data.uf
    };
    console.log(endereco);
  })
  .catch(error => {
    console.error(error);
  });
