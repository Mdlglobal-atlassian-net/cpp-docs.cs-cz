---
title: 'Ovládací prvky MFC ActiveX: Distribuce ovládacích prvků ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7c6658c972b9d9cdeececd43a89ac424964d2289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC – ovládací prvky ActiveX: Distribuce ovládacích prvků ActiveX
Tento článek popisuje několik problémy související s Redistribuce ovládacích prvků ActiveX:  
  
-   [ANSI nebo Unicode řízení verze](#_core_ansi_or_unicode_control_versions)  
  
-   [Instalace ovládacích prvků ActiveX a Redistributable knihovny DLL](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [Registrace ovládacích prvků](#_core_registering_controls)  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI nebo Unicode řízení verze  
 Musíte se rozhodnout, jestli se pro odeslání ANSI nebo Unicode verze ovládacího prvku, nebo obojí. Toto rozhodnutí vychází přenositelnost faktory, které jsou obsažené v znakové sady ANSI a Unicode.  
  
 Ovládací prvky ANSI, které fungují na všech operačních systémech Win32, umožňují pro maximální přenositelnost mezi různými operačními systémy Win32. Ovládací prvky Unicode fungovat na pouze systém Windows NT (verze 3.51 nebo novější), ale není v systému Windows 95 nebo Windows 98. Pokud přenositelnost je vaším hlavním zájmem ovládací prvky lodě ANSI. Pokud vaše ovládací prvky se spustí pouze v systému Windows NT, můžete zaslat ovládací prvky kódování Unicode. Může se také rozhodnout dodávat i a mít aplikaci nainstalovat na verzi, která je nejvhodnější pro uživatele operačního systému.  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Instalace ovládacích prvků ActiveX a Redistributable knihovny DLL  
 Instalační program, který zadáte s ovládacími prvky ActiveX by měl vytvořit podadresář speciální v adresáři systému Windows a nainstalujte ovládací prvky. OCX soubory v ní.  
  
> [!NOTE]
>  Použití Windows **GetWindowsDirectory** rozhraní API v instalačním programu se získat název adresáře systému Windows. Můžete k odvozování z názvu společnosti nebo produktu, název podadresáře.  
  
 Instalační program musíte nainstalovat potřebné distribuovatelné soubory DLL v adresáři systému Windows. Pokud některá z knihoven DLL již uloženy v počítači uživatele, instalační program by měl porovnat jejich verze s verzemi, které instalujete. Přeinstalujte soubor pouze v případě jeho číslo verze je vyšší než soubor již nainstalován.  
  
 Protože ovládací prvky ActiveX, je možné použít pouze v OLE – aplikace typu kontejner, je nutné distribuovat úplnou sadu knihoven DLL OLE s ovládacími prvky. Můžete předpokládat, že obsahující aplikace (nebo samotného operačního systému) má standardní OLE knihoven DLL nainstalována.  
  
##  <a name="_core_registering_controls"></a> Registrace ovládacích prvků  
 Před použitím ovládacího prvku, příslušné položky musí být vytvářeny pro něj registrační databázi systému Windows. Některé – kontejnery ovládacích prvků ActiveX poskytují položku nabídky uživatelům zaregistrovat nové ovládací prvky, ale tato funkce nemusí být k dispozici v všechny kontejnery. Proto můžete chtít zaregistrovat ovládací prvky, kdy se instalují vaší instalačního programu.  
  
 Pokud dáváte přednost, můžete napsat vaše instalační program k registraci ovládacího prvku přímo místo.  
  
 Použití **LoadLibrary** rozhraní API systému Windows se načíst knihovnu DLL ovládacího prvku. Pak pomocí **GetProcAddress** získat adresu funkce "DllRegisterServer". Nakonec zavolejte `DllRegisterServer` funkce. Následující příklad kódu ukazuje jeden možný způsob, kde `hLib` uloží popisovač řízení knihovny, a `lpDllEntryPoint` ukládá adresu funkce "DllRegisterServer".  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 Výhodou registrace ovládacího prvku přímo je, není nutné k vyvolání a načtení samostatný proces (konkrétně, REGSVR32), čímž se zkrátí doba instalace. Kromě toho protože registrace je interní proces, instalační program může zpracovávat chyby a může nepředpokládaného situacích lepší, než externího procesu.  
  
> [!NOTE]
>  Dříve, než instalační program nainstaluje ovládací prvek ActiveX, by měly volat **provedení**. Po dokončení instalačního programu volání **OleUnitialize**. Tím se zajistí OLE systémové knihovny DLL ve správném stavu pro registraci ovládacího prvku ActiveX.  
  
 Byste měli zaregistrovat MFCx0.DLL.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

