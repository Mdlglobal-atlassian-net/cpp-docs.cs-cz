---
title: "Vytváření programů využívajících vzdálenou automatizaci | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Remote Automation, creating programs
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86a9b9f4dccaaa3a97366dffb11955d3b148aff5
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="creating-programs-that-use-remote-automation"></a>Vytváření programů využívajících vzdálenou automatizaci
Jakýkoli objekt automatizace a jakýkoli řadič automatizace je možné používat vzdálenou automatizaci bez jakékoli změny do zdrojového kódu, bez nutnosti rekompilace a bez nutnosti opakované propojování. Až budete mít instalačního programu, která funguje místně (který je na stejném počítači), musí projít jenom pár kroků provést vzdáleně.  
  
#### <a name="to-execute-the-remote-automation-object"></a>Spustit objekt Vzdálená automatizace  
  
1.  Registrace aplikace na klientský počítač nebo počítače.  
  
2.  Konfigurace klienta přístup k použití vzdáleného serveru.  
  
3.  Instalace a registrace v aplikaci na počítač serveru nebo počítače.  
  
4.  Konfigurace serveru pro povolení vzdálené aktivace.  
  
5.  Správce automatizace nainstalujte na server počítač(e).  
  
6.  Správce automatizace spusťte na serverech.  
  
7.  Spuštění aplikace na mailového klienta.  
  
 Krok 1 nejsnáze načtením a provádění serverové aplikace v klientském počítači, protože většina serverů jsou vlastní registrace. Je-li otestovat nastavení místně této fáze je předem, již dokončena. Pokud je serverová aplikace není vlastní registrace, můžete chtít provést tak. Jinak musíte zadat soubor registrace, který můžete spustit místního uživatele k provedení tohoto kroku. Pokud uděláte ani jeden z těchto věcí, vy nebo správce bude nutné ručně upravit registr postup, který se nedoporučuje pro všechny ale nejpokročilejší uživatele.  
  
 Krok 2 zahrnuje použití Správce připojení vzdálené automatizace (RAC). Spusťte správce RAC a zkontrolujte, zda je na kartě připojení serveru nejvyšší. Poté vyhledejte položku pro objekt serveru v **třídy OLE** podokně a klepněte na něj. Pak přejděte na **síťová adresa** pole se seznamem a zadejte název počítače serveru, na kterém se spustí vzdálené spustitelný soubor. Například můžete zadat \\\MyServer sem. Z uvedeného seznamu zvolte příslušné síťový protokol. Budete muset obraťte se na správce sítě k určení, protokol, který se doporučuje. V mnoha případech bude protokol TCP/IP. Nakonec můžete vybrat úroveň ověřování. Ve většině případů bude vlevo jako (žádné), nebo výchozí hodnotu. Nyní klikněte pravým tlačítkem myši na server v **třídy OLE** podokně. Vznikne tak místní nabídky, ze kterého můžete vybrat místní nebo vzdálené operace. Vyberte vzdálené.  
  
 Krok 3 zahrnuje správně instalaci a registraci serverovou aplikaci na vybraném serveru počítače nebo počítače. Znovu Pokud je aplikace vlastní registrace, její provedení jednou také se zaregistruje ho.  
  
 Krok 4 zahrnuje konfiguraci serveru tak, aby vzdálené spuštění. Spusťte správce RAC na serveru a ujistěte se, že **klientský přístup** karta je aktivní. Vyberte model aktivace, který chcete (obvykle **povolit vzdálené vytvoří pomocí klíče**. Pokud zvolíte tuto možnost, musíte taky kliknout na odkaz **povolit vzdálená aktivace** zaškrtávací políčko se nastavit hodnotu položky registru na 'Y'). Pokud zvolíte možnost povolit vzdálené vytvoří (ACL), máte také možnost Upravit seznam ACL vynucením **upravit seznam ACL** tlačítko.  
  
 Povolit vzdálené automatizace pro práci, pak musíte zajistit, že Správce automatizace je nainstalovaná a spuštěná na počítači serveru nebo počítače. Pokud není nainstalována, zkopírujte AUTMGR32. EXE k adresáři systému Windows. Informace o tom, jak to provést, najdete v článku [instalace vzdálené automatizace](../mfc/remote-automation-installation.md). Spuštění vzdálené automatizace, spusťte Správce automatizace. Zobrazí okno malé stavu, ve kterém se zobrazí počet zpráv. Po jeho spuštění, minimalizuje se sám sebe. Pokud chcete nadále zobrazovat informace o stavu, můžete kliknout **Správce automatizace** karta na hlavním panelu obnovte okno.  
  
 Posledním krokem je v klientském počítači spustit klientskou aplikaci. Pokud jste postupovali podle kroků výše, měl by připojení k serveru objektu a provést přesně stejně jako místně, i když je trochu nižší.  
  
 Všimněte si, že RAC Manager také umožňuje přepínat mezi vzdálené automatizace a modelu distributed COM (DCOM, na těchto platformách, které podporují model DCOM) s jedním kliknutím přepínače. Pokud si zvolíte DCOM, můžete nastavit další možnosti konfigurace. Naleznete v dokumentaci k modelu DCOM pro další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálená automatizace](../mfc/remote-automation.md)   
 [Spuštění vzdálené automatizace s použitím příkazů AUTOCLIK a AUTODRIV](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)

