---
title: 'MFC – ovládací prvky ActiveX: Distribuce ovládacích prvků ActiveX | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d400bf09d2fd3484b573112d87735ce0a74d944e
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534895"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC – ovládací prvky ActiveX: Distribuce ovládacích prvků ActiveX
Tento článek popisuje několik problémy související s Redistribuce souborů ovládacích prvků ActiveX:  
  
-   [ANSI nebo Unicode ovládací prvek verze](#_core_ansi_or_unicode_control_versions)  
  
-   [Instalace ovládacích prvků ActiveX a distribuovatelné knihovny DLL](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [Registrace ovládacích prvků](#_core_registering_controls)  


>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI nebo Unicode ovládací prvek verze  
 Musíte se rozhodnout, jestli se k odeslání ANSI nebo Unicode verze ovládacího prvku, nebo obojí. Toto rozhodnutí je na základě přenositelnost faktorů vyplývajících z znakové sady ANSI a Unicode.  
  
 Ovládací prvky ANSI, které pracují na všechny operační systémy Win32, umožňují pro zajištění maximální přenositelnosti mezi různé operační systémy Win32. Ovládací prvky Unicode fungovat pouze Windows NT (verze 3.51, aktualizace nebo novější), ale ne Windows 95 nebo Windows 98. Je-li přenositelnost je vaším hlavním zájmem příjemce ANSI ovládací prvky. Pokud své ovládací prvky se spustí pouze v systémech Windows NT, můžete zaslat Unicode ovládací prvky. Může se také rozhodnout obě dodávání a máte svou aplikaci nainstalovat verzi operačního systému uživatele nejvhodnější.  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Instalace ovládacích prvků ActiveX a distribuovatelné knihovny DLL  
 Instalační program, který poskytnete s ovládacími prvky ActiveX byste vytvořit zvláštní podadresáře adresáře, Windows a nainstalovat ovládací prvky. OCX soubory v něm.  
  
> [!NOTE]
>  Použít Windows `GetWindowsDirectory` rozhraní API ve vašem instalačním programu získat název adresáře Windows. Můžete odvozovat od názvu vaši společnost nebo produkt název podadresáře.  
  
 Instalační program musíte nainstalovat potřebné distribuovatelné soubory knihovny DLL v adresáři systému Windows. Pokud některé z knihoven DLL, která jsou již přítomny v počítači uživatele, instalační program by porovnání jejich verzí s verzí, kterou instalujete. Znovu nainstalujte soubor pouze v případě, že její číslo verze je vyšší než již nainstalovaného souboru.  
  
 Protože – ovládací prvky ActiveX lze použít pouze v aplikacích kontejneru OLE, není nutné distribuovat úplnou sadu knihoven OLE DLL s ovládacími prvky. Můžete předpokládat, obsahující aplikaci (nebo samotného operačního systému) má standardní OLE knihovny DLL nainstalované.  
  
##  <a name="_core_registering_controls"></a> Registrace ovládacích prvků  
 Před použitím ovládacího prvku, musí pro něj vytvořit odpovídající položky v registrační databázi Windows. Některé – kontejnery ovládacích prvků ActiveX poskytují položku nabídky pro uživatele k registraci nové ovládací prvky, ale tato funkce nemusí být k dispozici ve všech kontejnerech. Proto můžete instalační program tak, zaregistrujte ovládací prvky, kdy se instalují.  
  
 Pokud dáváte přednost, můžete napsat program Instalační program k registraci ovládacího prvku přímo místo.  
  
 Použití `LoadLibrary` rozhraní Windows API načíst knihovnu DLL ovládacího prvku. Pak pomocí `GetProcAddress` pro získání adresy funkce "DllRegisterServer". Nakonec proveďte volání `DllRegisterServer` funkce. Následující příklad kódu ukazuje jeden možný způsob, ve kterém `hLib` uloží popisovač knihovny ovládacích prvků a `lpDllEntryPoint` ukládá adresu funkce "DllRegisterServer".  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 Výhodou přímo registrace ovládacího prvku je, že nepotřebujete k vyvolání a načtení samostatný proces (konkrétně REGSVR32), snižuje čas instalace. Navíc vzhledem k tomu, že registrace je interní proces, instalační program může zpracovávat chyby a nepředvídané situacích lepší než externí proces můžete.  
  
> [!NOTE]
>  Předtím, než instalační program nainstaluje ovládacího prvku ActiveX, měla by volat `OleInitialize`. Po dokončení instalačního programu volat `OleUnitialize`. Tím se zajistí, že OLE systémové knihovny DLL jsou ve stavu správné pro registraci ovládacího prvku ActiveX.  
  
 Byste měli zaregistrovat MFCx0.DLL.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

