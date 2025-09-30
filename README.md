# 🚀 CT_Indirect_Syscalls

⚠️ **Aviso importante:** Este projeto é apenas para **fins educacionais** e de pesquisa em ambientes controlados. O código demonstra como alocar memória executável em tempo de execução e executar bytes arbitrários (shellcode). Técnicas como esta podem ser usadas tanto em contextos legítimos (JITs, loaders in-memory, segurança ofensiva/defensiva) quanto por malware. **Não use em sistemas de produção ou sem autorização.**

---

## 🎯 Objetivo

Este projeto mostra como:

* 🔍 Obter endereços de funções nativas do Windows (`ntdll.dll`).
* 🧩 Usar `NtAllocateVirtualMemory` para alocar memória executável.
* ✍️ Escrever bytes (shellcode) diretamente nessa memória.
* 🧵 Criar uma nova thread que inicia no shellcode (`NtCreateThreadEx`).
* ⏳ Aguardar a execução da thread (`NtWaitForSingleObject`).

👉 O shellcode presente no exemplo é **incompleto** e não faz nada útil. A ideia é apenas **demonstrar a técnica**.

---

## ⚙️ Requisitos

* 🪟 Windows (32 ou 64 bits).
* 🛠️ Compilador C (Visual Studio / MSVC recomendado).
* 🔑 Permissões para compilar e rodar binários.

---

## ▶️ Execução

1. Abra uma **máquina virtual** ou **sandbox segura** 🛡️.
2. Compile o projeto.
3. Rode o binário:

```bat
PE-Loader.exe
```

📌 **Importante:** só use shellcodes que você entende e que sejam seguros.

---

## 🔎 Como funciona o `main.c`

1. Carrega endereços de funções `Nt*` a partir de `ntdll.dll`.
2. Usa `NtAllocateVirtualMemory` para reservar memória RWX.
3. Copia o array de bytes (`shellcode[]`) para lá.
4. Cria uma thread para executar esse código.
5. Espera a thread terminar.

⚠️ O comportamento real depende 100% do shellcode.

---

## 🛡️ Observações de segurança

* 🚫 O shellcode fornecido é apenas 3 bytes (`"\xfc\x48\x83"`), não faz nada funcional.
* 🧨 Técnicas assim são detectadas por antivírus e EDR.
* 🔒 Executar memória marcada como executável pode ser bloqueado por políticas modernas do Windows.
* 🙋‍♂️ Você é **responsável pelo uso** deste código.

---

## 💌 Contato

**Caso queira me contatar ou precise de algum serviço, me encontre nas seguintes plataformas:**

**Usuário do Discord: 4wj.**

**Instagram: @glowwz9**

**E-mail: vliyanie1337@proton.me**
