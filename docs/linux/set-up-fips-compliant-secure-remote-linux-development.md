---
title: Nastavení zabezpečeného vzdáleného nasazení systému Linux kompatibilního se standardem FIPS
description: Jak nastavit kryptografické připojení kompatibilní se standardem FIPS mezi sadou Visual Studio a počítačem se systémem Linux pro vzdálené vývoj.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520891"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Nastavení zabezpečeného vzdáleného nasazení systému Linux kompatibilního se standardem FIPS

::: moniker range="<=vs-2017"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším. Zabezpečený vzdálený vývoj pro Linux se standardem FIPS je k dispozici v systému Visual Studio 2019 verze 16,5 a novější.

::: moniker-end

::: moniker range="vs-2019"

Publikace standardu FIPS (Federal Information Processing Standard) 140-2 je standard státní správy USA pro kryptografické moduly. Implementace standardu jsou ověřovány pomocí NIST. Systém Windows [ověřil podporu pro kryptografické moduly kompatibilní se standardem FIPS](/windows/security/threat-protection/fips-140-validation). V aplikaci Visual Studio 2019 verze 16,5 a novější můžete pro vzdálené vývoj použít zabezpečené kryptografické připojení kompatibilní se standardem FIPS pro systém Linux.

Tady je postup nastavení zabezpečeného připojení kompatibilního se standardem FIPS mezi sadou Visual Studio a vzdáleným systémem Linux. Tato příručka se vztahuje při sestavování projektů CMake nebo MSBuild Linux v sadě Visual Studio. Tento článek je verzí pokynů pro připojení kompatibilní se standardem FIPS v tématu [připojení ke vzdálenému počítači se systémem Linux](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Příprava připojení kompatibilního se standardem FIPS

Některá příprava je nutná k použití kryptograficky zabezpečeného připojení SSH kompatibilního se standardem FIPS mezi Visual Studio a vaším vzdáleným systémem Linux. V případě dodržování předpisů FIPS-140-2 podporuje Visual Studio pouze klíče RSA.

Příklady v tomto článku používají Ubuntu 18,04 LTS s OpenSSH serverem verze 7,6. Nicméně pokyny by měly být stejné pro všechny distribuce s využitím středně poslední verze OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Nastavení serveru SSH ve vzdáleném systému

1. V systému Linux nainstalujte a spusťte server OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Pokud byste chtěli, aby se server SSH spouštěl automaticky při spuštění systému, povolte ho pomocí systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

1. Otevřete */etc/ssh/sshd_config* jako kořen. Upravit (nebo přidat, pokud neexistují) následující řádky:

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > SSH-RSA je jediným algoritmem klíče hostitele kompatibilního se standardem FIPS VS podporuje. Algoritmy AES\*-centra jsou také kompatibilní se standardem FIPS, ale implementace v aplikaci Visual Studio není schválená. Algoritmy výměny klíčů\* ECDH jsou kompatibilní se standardem FIPS, ale Visual Studio je nepodporuje.

   Nejste omezeni na tyto možnosti. SSH můžete nakonfigurovat tak, aby používala další šifry, algoritmy klíčů hostitele atd. Některé další důležité možnosti zabezpečení, které je vhodné zvážit, jsou `PermitRootLogin`, `PasswordAuthentication`a `PermitEmptyPasswords`. Další informace najdete na stránce muž pro sshd_config nebo v článku [Konfigurace serveru SSH](https://www.ssh.com/ssh/sshd_config).

1. Po uložení a zavření sshd_config restartujte server SSH, aby se nová konfigurace projevila:

   ```bash
   sudo service ssh restart
   ```

V dalším kroku vytvoříte pár klíčů RSA na počítači s Windows. Pak zkopírujete veřejný klíč do vzdáleného systému Linux, který bude používat SSH.

### <a name="to-create-and-use-an-rsa-key-file"></a>Vytvoření a použití souboru klíče RSA

1. Na počítači s Windows vygenerujte dvojici veřejného a privátního klíče RSA pomocí tohoto příkazu:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   Příkaz vytvoří veřejný klíč a privátní klíč. Ve výchozím nastavení se klíče ukládají do *% USERPROFILE%\\. ssh\\id_rsa* a *% USERPROFILE%\\. ssh\\id_rsa. pub*. (V PowerShellu použijte `$env:USERPROFILE` místo `%USERPROFILE%`makra cmd). Pokud změníte název klíče, použijte změněný název v následujících krocích.  Pro zvýšení zabezpečení doporučujeme použít přístupové heslo.

1. Z Windows zkopírujte veřejný klíč do počítače se systémem Linux:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. V systému Linux přidejte klíč do seznamu autorizovaných klíčů a ujistěte se, že soubor má správná oprávnění:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Nyní můžete otestovat a zjistit, zda nový klíč funguje v SSH. Použijte ho pro přihlášení z Windows:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Úspěšně jste nastavili SSH, vytvořili a nasadili šifrovací klíče a otestovali jste připojení. Teď jste připraveni nastavit připojení sady Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Připojení ke vzdálenému systému v aplikaci Visual Studio

1. V aplikaci Visual Studio vyberte **nástroje > možnosti** na řádku nabídek a otevřete tak dialogové okno **Možnosti** . Pak vyberte pro **různé platformy > Správce připojení** a otevřete dialogové okno Správce připojení.

   Pokud jste ještě před prvním sestavením projektu nevytvořili připojení v sadě Visual Studio, Visual Studio otevře pro vás dialog Správce připojení.

1. V dialogovém okně Správce připojení kliknutím na tlačítko **Přidat** přidejte nové připojení.

   ![Správce připojení](media/settings_connectionmanager.png)

   Zobrazí se okno **připojit ke vzdálenému systému** .

   ![Připojit ke vzdálenému systému](media/connect.png)

1. V dialogovém okně **připojit ke vzdálenému systému** zadejte podrobnosti o připojení ke vzdálenému počítači.

   | Entry | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, na kterém běží služba SSH, obvykle 22
   | **Uživatelské jméno**           | Uživatel, který se má ověřit jako
   | **Typ ověřování** | Zvolit privátní klíč pro připojení kompatibilní se standardem FIPS
   | **Soubor privátního klíče**    | Soubor privátního klíče vytvořený pro připojení SSH
   | **Hesel**          | Přístupové heslo použité s privátním klíčem vybraným výše

   Změňte typ ověřování na **privátní klíč**. Do pole **soubor privátního klíče** zadejte cestu k privátnímu klíči. Pomocí tlačítka **Procházet** můžete místo toho přejít k souboru privátního klíče. Pak zadejte heslo používané k zašifrování souboru privátního klíče v poli **heslo** .

1. Klikněte na tlačítko **připojit** a pokuste se připojit ke vzdálenému počítači.

   Pokud je připojení úspěšné, Visual Studio nakonfiguruje technologii IntelliSense na používání vzdálených hlaviček. Další informace najdete v tématu [IntelliSense pro hlavičky ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se připojení nepovede, jsou vstupní pole, která je potřeba změnit, označená červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Další informace o řešení potíží s připojením najdete v tématu [připojení ke vzdálenému počítači se systémem Linux](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Nástroj příkazového řádku pro správce připojení  

**Visual Studio 2019 verze 16,5 nebo novější**: ConnectionManager. exe je nástroj příkazového řádku pro správu připojení vzdáleného vývoje mimo sadu Visual Studio. Je vhodný pro úlohy, jako je například zřízení nového vývojového počítače. Nebo ho můžete použít k nastavení sady Visual Studio pro průběžnou integraci. Příklady a kompletní odkaz na příkaz ConnectionManager naleznete v tématu [ConnectionManager reference](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Volitelné: povolí nebo zakáže režim FIPS.

V systému Windows je možné povolit režim FIPS globálně.

1. Pokud chcete povolit režim FIPS, otevřete dialogové okno spustit stisknutím **Windows + R** a pak spusťte gpedit. msc.

1. Rozbalte položku **místní počítač zásada > konfigurace počítače > nastavení systému Windows > nastavení zabezpečení > místní zásady** a vyberte **Možnosti zabezpečení**.

1. V části **zásady**vyberte **Kryptografie systému: pro šifrování, algoritmus hash a podepisování použijte algoritmy kompatibilní se standardem FIPS**a potom stiskněte **ENTER** . otevře se dialogové okno.

1. Na kartě **místní nastavení zabezpečení** vyberte možnost **povoleno** nebo **zakázáno**a pak kliknutím na **tlačítko OK** uložte změny.

> [!WARNING]
> Povolení režimu FIPS může způsobit, že některé aplikace přeruší nebo se chovají neočekávaně. Další informace najdete v blogovém příspěvku, [Proč už nedoporučujeme "režim FIPS"](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037).

## <a name="additional-resources"></a>Další materiály a zdroje informací

[Dokumentace Microsoftu k ověřování FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: požadavky na zabezpečení pro kryptografické moduly](https://csrc.nist.gov/publications/detail/fips/140/2/final) (z NIST)

[Ověřovací program kryptografického algoritmu: poznámky k ověření](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (z NIST)

Blogový příspěvek Microsoftu s tím, [že už nedoporučujeme používat režim FIPS](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[Konfigurace serveru SSH](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Viz také

[Konfigurace\ projektu pro Linux](configure-a-linux-project.md)
[Konfigurace projektu Linux cmake](cmake-linux-project.md)\
[Připojte se ke vzdálenému počítači se systémem Linux](connect-to-your-remote-linux-computer.md)\
[Nasazení, spuštění a ladění projektu pro Linux](deploy-run-and-debug-your-linux-project.md)\
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
