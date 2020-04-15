---
title: Nastavení zabezpečeného vzdáleného vývoje pro Linux kompatibilního se standardem FIPS
description: Jak nastavit kryptografické připojení kompatibilní s FIPS mezi Visual Studio a linuxovým počítačem pro vzdálený vývoj.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520891"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Nastavení zabezpečeného vzdáleného vývoje pro Linux kompatibilního se standardem FIPS

::: moniker range="<=vs-2017"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším. Vývoj zabezpečeného vzdáleného Linuxu kompatibilnímu s FIPS je k dispozici ve Visual Studiu 2019 verze 16.5 a novějších.

::: moniker-end

::: moniker range="vs-2019"

Federal Information Processing Standard (FIPS) Publication 140-2 je standard vlády USA pro kryptografické moduly. Implementace standardu jsou validovány NIST. Systém Windows [ověřil podporu kryptografických modulů kompatibilních s FIPS](/windows/security/threat-protection/fips-140-validation). Ve Visual Studiu 2019 verze 16.5 a novějších můžete pro vzdálený vývoj použít zabezpečené kryptografické připojení kompatibilní s FIPS se systémem Linux.

Tady je postup, jak nastavit zabezpečené připojení kompatibilní s FIPS mezi Visual Studio a vzdáleným systémem Linux. Tato příručka je použitelná při vytváření projektů CMake nebo MSBuild Linux v sadě Visual Studio. Tento článek je kompatibilní s fips verzí pokynů pro připojení v [části Připojit ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Příprava připojení vyhovujícího FIPS

Některé přípravy je nutné použít FIPS kompatibilní, kryptograficky zabezpečené ssh připojení mezi Visual Studio a vzdálený systém Linux. Pro dodržování předpisů FIPS-140-2 Visual Studio podporuje pouze rsa klíče.

Příklady v tomto článku používají Ubuntu 18.04 LTS se serverem OpenSSH verze 7.6. Nicméně, pokyny by měly být stejné pro všechny distro pomocí mírně poslední verzi OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Nastavení serveru SSH ve vzdáleném systému

1. V systému Linux nainstalujte a spusťte server OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Pokud chcete, aby se server ssh spouštěl automaticky při spuštění systému, povolte jej pomocí systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

1. Otevřít */etc/ssh/sshd_config* jako kořen. Upravte (nebo přidejte, pokud neexistují) následující řádky:

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa je jediný algoritmus klíče hostitele kompatibilní s FIPS, který VS podporuje. Aes\*-ctr algoritmy jsou také kompatibilní fips, ale implementace v sadě Visual Studio není schválen. Algoritmy výměny klíčů ecdh-\* jsou kompatibilní s FIPS, ale Visual Studio je nepodporuje.

   Nejste omezeni na tyto možnosti. Ssh můžete nakonfigurovat tak, aby používal další šifry, algoritmy klíče hostitele a tak dále. Některé další relevantní možnosti zabezpečení, `PermitRootLogin` `PasswordAuthentication`které `PermitEmptyPasswords`můžete zvážit, jsou , a . Další informace naleznete na stránce man pro sshd_config nebo v článku [Konfigurace serveru SSH](https://www.ssh.com/ssh/sshd_config).

1. Po uložení a zavření sshd_config restartujte server ssh a použijte novou konfiguraci:

   ```bash
   sudo service ssh restart
   ```

Dále vytvoříte pár klíčů RSA v počítači se systémem Windows. Pak zkopírujete veřejný klíč do vzdáleného systému Linux pro použití ssh.

### <a name="to-create-and-use-an-rsa-key-file"></a>Vytvoření a použití souboru klíče RSA

1. V počítači se systémem Windows vygenerujte dvojici klíčů RSA veřejné ho a soukromé pomocí tohoto příkazu:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   Příkaz vytvoří veřejný klíč a soukromý klíč. Ve výchozím nastavení jsou klíče uloženy do *\\%USERPROFILE%\\.ssh id_rsa* a *%USERPROFILE%\\.ssh\\id_rsa.pub*. (V powershellu `$env:USERPROFILE` použijte místo makra `%USERPROFILE%`cmd) Pokud změníte název klíče, použijte změněný název v následujících krocích.  Pro zvýšení zabezpečení doporučujeme použít přístupové heslo.

1. Z Windows zkopírujte veřejný klíč do počítače s Linuxem:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. V systému Linux přidejte klíč do seznamu autorizovaných klíčů a ujistěte se, že soubor má správná oprávnění:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Nyní můžete vyzkoušet, zda nový klíč funguje v ssh. Použijte ho k přihlášení z Windows:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Úspěšně jste nastavili šifrovací klíče ssh, vytvořili a nasadili a otestovali připojení. Nyní jste připraveni nastavit připojení sady Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Připojení ke vzdálenému systému v sadě Visual Studio

1. V Sadě Visual Studio zvolte **Nástroje > Možnosti** na řádku nabídek a otevřete dialogové okno **Volby.** Pak vyberte **Cross Platform > Connection Manager** otevřete dialogové okno Connection Manager.

   Pokud jste připojení v sadě Visual Studio ještě nenastavili, otevře visual studio při prvním sestavení projektu dialogové okno Connection Manager.

1. V dialogovém okně Správce připojení zvolte tlačítko **Přidat** a přidejte nové připojení.

   ![Správce připojení](media/settings_connectionmanager.png)

   Zobrazí se okno **Připojit ke vzdálenému systému.**

   ![Připojení ke vzdálenému systému](media/connect.png)

1. V dialogovém okně **Připojit ke vzdálenému systému** zadejte podrobnosti o připojení vzdáleného počítače.

   | Záznam | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, na který je spuštěna služba SSH, obvykle 22
   | **Uživatelské jméno**           | Uživatel k ověření jako
   | **Typ ověřování** | Zvolte soukromý klíč pro připojení kompatibilní s FIPS.
   | **Soubor soukromého klíče**    | Soubor soukromého klíče vytvořený pro připojení ssh
   | **Heslo**          | Přístupové heslo použité s výše vybraným soukromým klíčem

   Změňte typ ověřování na **soukromý klíč**. Do pole **Soubor soukromého klíče** zadejte cestu k soukromému klíči. Místo toho můžete pomocí tlačítka **Procházet** přejít do souboru soukromého klíče. Poté zadejte přístupové heslo použité k zašifrování souboru soukromého klíče do pole **Přístupové heslo.**

1. Chcete-li se pokusit o připojení ke vzdálenému počítači, zvolte tlačítko **Připojit.**

   Pokud je připojení úspěšné, Visual Studio nakonfiguruje intelliSense používat vzdálené záhlaví. Další informace naleznete v tématu [IntelliSense pro záhlaví ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se připojení nezdaří, jsou pole, která je třeba změnit, označena červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Další informace o řešení potíží s připojením naleznete v tématu [Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Nástroj příkazového řádku pro správce připojení  

**Visual Studio 2019 verze 16.5 nebo novější**: ConnectionManager.exe je nástroj příkazového řádku pro správu vzdálených vývojových připojení mimo Visual Studio. Je to užitečné pro úkoly, jako je zřizování nového vývojového počítače. Nebo ji můžete použít k nastavení sady Visual Studio pro průběžnou integraci. Příklady a úplný odkaz na příkaz ConnectionManager naleznete v [tématu ConnectionManager reference](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Volitelné: Povolení nebo zakázání režimu FIPS

Režim FIPS je možné povolit globálně v systému Windows.

1. Chcete-li režim FIPS povolit, otevřete stisknutím **kláves Windows+R** dialogové okno Spustit a spusťte soubor gpedit.msc.

1. Rozbalte **položku Místní zásady > Konfigurace počítače > Nastavení systému Windows > Nastavení zabezpečení > místních zásad** a vyberte **možnosti zabezpečení**.

1. V části **Zásady**vyberte **Možnost Systémová kryptografie: Pomocí algoritmů kompatibilních s FIPS pro šifrování, algoritmus hash a podepisování**a stisknutím **klávesy Enter** otevřete jeho dialogové okno.

1. Na kartě **Nastavení místního zabezpečení** vyberte **Možnost Povoleno** nebo **Zakázáno**a pak zvolte **OK,** chcete-li změny uložit.

> [!WARNING]
> Povolení režimu FIPS může způsobit, že některé aplikace přerušit nebo se chovat neočekávaně. Další informace naleznete v příspěvku na blogu [Why We're Not Doporučování "režim FIPS" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037).

## <a name="additional-resources"></a>Další zdroje

[Dokumentace společnosti Microsoft k ověření FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: Bezpečnostní požadavky pro kryptografické moduly](https://csrc.nist.gov/publications/detail/fips/140/2/final) (od NIST)

[Program ověřování kryptografických algoritmů: Ověřovací poznámky](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (od NIST)

Microsoft blog post na [Proč nejsme nedoporučujeme "FIPS režim" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[Konfigurace serveru SSH](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Viz také

[Konfigurace projektu Linuxu](configure-a-linux-project.md)\
[Konfigurace projektu Linux CMake](cmake-linux-project.md)\
[Připojení ke vzdálenému počítači s Linuxem](connect-to-your-remote-linux-computer.md)\
[Nasazení, spuštění a ladění projektu Linuxu](deploy-run-and-debug-your-linux-project.md)\
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
