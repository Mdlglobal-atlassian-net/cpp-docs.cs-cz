---
title: "Nainstalujte chybějící Microsoft Visual C++ Runtime knihovny DLL | Microsoft Docs"
description: "Jak najít a nainstalovat chybějící knihovny DLL modulu runtime Visual C++."
ms.date: 08/30/2017
ms.topic: article
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d40e1594b2190d4bbfd2fe52fddaad04af527573
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2018
---
# <a name="install-a-missing-microsoft-visual-c-runtime-dll"></a>Nainstalujte chybějící Microsoft Visual C++ Runtime knihovny DLL

Programy, které jsou napsané v Microsoft Visual C++ často vyžadují některé další soubory modulu runtime knihoven Visual C++, knihovny DLL, je třeba spustit. Tyto modulu runtime knihoven DLL jsou k dispozici v *Redistributable Package*, knihovna soubor instalačního programu pro každou verzi Visual C++. Distribuovatelný balíček vyžaduje žádné program zahrnuté jeho instalační služby. Pokud není, v některých případech můžete nainstalovat redistribuovatelný balíček sami a opravte chybu systému při spuštění programu. 

Můžete zjistit, že programu chybí Visual C++ runtime knihoven DLL, pokud dojde k chybě systému při spuštění aplikace s informacemi o tom něco jako "program nelze spustit, protože chybí VCRuntime140.dll z vašeho počítače". Tento problém můžete opraven často, odinstalace programu a potom instalaci opakujte. Důrazně doporučujeme při tomto kroku nejprve než ostatní potenciální opravy.

Distribuovatelný balíček nainstalované programy, které někdy je zastaralý. Společnost Microsoft zpřístupňuje aktualizované verze modulu runtime knihoven DLL od času na adresu chyby a problémy se zabezpečením. Aby počítače se spuštěným systémem bezpečně a správně, je vhodné použít nejnovější aktualizace pro všechny knihovny DLL pro modul runtime. Zkontrolujte, zda je k dispozici pro váš program, který může poskytnout této aktualizace vám aktualizovaný instalační program. Pokud existuje, použijte aktualizovaný instalační program znovu nainstalovat program.

Program přeinstalovat neznamená, že systémová chyba zmizí, potom instalační program možná je poškozený nebo poškozený nebo modul runtime knihovny DLL ve vašem počítači může být poškozena. Zkuste stáhnout novou kopii instalačního programu k aplikaci a použít ho k opětovné instalaci první. Pokud to nepomůže, nebo instalační program není k dispozici, pak může být smysl zkontrolujte Microsoft Visual C++ Redistributable instalací ve vašem počítači. 

Tato tabulka obsahuje seznam knihoven DLL, které jsou součástí jedné nebo více Distribuovatelné balíčky, spolu s odkazy na stáhnout kopii redistribuovatelného balíčku. Před stažením novou kopii distribuovatelného balíčku, měli byste vidět, pokud existující instalaci můžete opravit.

|Chybí knihovna DLL  |Distribuovatelný balíček  |
|---------|---------|
|atl80.dll<br />msvcm80.dll<br />msvcp80.dll<br />msvcr80.dll<br />mfc80.dll<br />mfc80u.dll<br />mfcm80.dll<br />mfcm80u.dll|[Microsoft Visual C++ 2005 Redistributable (x86)](https://www.microsoft.com/en-us/download/details.aspx?id=5638)<br />[Distribuovatelný balíček Microsoft Visual C++ 2005 (x64)](https://www.microsoft.com/en-us/download/details.aspx?id=18471)<br />[Aktualizace zabezpečení Microsoft Visual C++ 2005 Service Pack 1 Redistributable Package MFC](https://www.microsoft.com/en-us/download/details.aspx?id=26347)|
|atl90.dll<br />msvcr90.dll<br />msvcm90.dll<br />msvcp90.dll<br />mfc90.dll<br />mfc90u.dll<br />mfcmifc80.dll<br />mfcm90.dll<br />mfcm90u.dll|[Microsoft Visual C++ 2008 Redistributable - x86](https://www.microsoft.com/en-us/download/details.aspx?id=5582)<br />[Microsoft Visual C++ 2008 Redistributable - x64](https://www.microsoft.com/en-us/download/details.aspx?id=2092)<br />[Aktualizace zabezpečení Microsoft Visual C++ 2008 Service Pack 1 Redistributable Package MFC](https://www.microsoft.com/en-us/download/details.aspx?id=26368)|
|atl100.dll<br />msvcr100.dll<br />msvcp100.dll<br />msdia71.dll<br />vcomp100.dll<br />mfc100.dll<br />mfc100u.dll<br />mfcmifc80.dll<br />mfcm100.dll<br />mfcm100u.dll|[Microsoft Visual C++ 2010 x86 Redistributable](https://www.microsoft.com/en-us/download/details.aspx?id=8328)<br />[Microsoft Visual C++ 2010 x64 Redistributable](https://www.microsoft.com/en-us/download/details.aspx?id=13523)<br />[Aktualizace zabezpečení Microsoft Visual C++ 2010 Service Pack 1 Redistributable Package MFC](https://www.microsoft.com/en-us/download/details.aspx?id=26999)|
|atl110.dll<br />msvcr110.dll<br />msvcp110.dll<br />mfc110.dll<br />mfc110u.dll<br />mfcmifc80.dll<br />mfcm110.dll<br />mfcm110u.dll<br />concrt110.dll<br />vccorlib110.dll<br />vcamp110.dll<br />vcomp110.dll|[Microsoft Visual C++ 2012 Redistributable (pro Visual Studio 2012 Update 4)](https://www.microsoft.com/en-us/download/details.aspx?id=30679)|
|msvcr120.dll<br />msvcp120.dll<br />mfc120.dll<br />mfc120u.dll<br />mfcmifc80.dll<br />mfcm120.dll<br />mfcm120u.dll<br />concrt120.dll<br />vccorlib120.dll<br />vcamp120.dll<br />vcomp120.dll|[Microsoft Visual C++ 2013 Redistributable (odkazy na jednotlivé soubory ke stažení)](https://support.microsoft.com/en-us/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)<br />[Více-bajtové MFC knihovny pro Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770)<br />[Visual C++ Runtime 2013 pro Windows 8.1 zkušebně načtené aplikace (ZIP ke stažení)](http://download.microsoft.com/download/5/F/0/5F0F8404-9329-44A9-8176-ED6F7F746F25/VCLibs_Redist_Packages.zip)|
|vcruntime140.dll<br />vcruntime140_app.dll<br />msvcp140.dll<br />mfc140.dll<br />mfc140u.dll<br />mfcmifc80.dll<br />mfcm140.dll<br />mfcm140u.dll<br />concrt140.dll<br />vccorlib140.dll<br />vcamp140.dll<br />vcomp140.dll|[Microsoft Visual C++ 2017 Redistributable (x86)](https://go.microsoft.com/fwlink/?LinkId=746571)<br />[Microsoft Visual C++ 2017 Redistributable (x64)](https://go.microsoft.com/fwlink/?LinkId=746572)|
|msvcr100_clr0400.dll<br />msvcr110_clr0400.dll<br />msvcr120_clr0400.dll|[Stáhnout rozhraní .NET Framework](https://www.microsoft.com/net/download/framework)|

### <a name="to-repair-an-existing-redistributable-package"></a>Chcete-li opravit existující distribuovatelného balíčku

1. Otevřete ovládací panely. V systému Windows 10, zadejte *ovládací panely* v ploše vyhledávání ovládacího prvku na hlavním panelu a potom zvolte **ovládací panely** z možností.

2. V Ovládacích panelech vyberte **programy** > **programy a funkce**. Vyberte verzi Microsoft Visual C++ Redistributable odpovídající knihovnu DLL, kterou chybí. Pokud **změnu** tlačítko se zobrazí v horní části seznamu, vyberte ho. Pokud je jediná volba **odinstalovat**, nelze opravit tuto verzi distribuovatelného balíčku.

3. Zvolte **Repair** v dialogovém okně nastavení pro redistribuovatelného balíčku. Musíte restartovat po dokončení opravy. 