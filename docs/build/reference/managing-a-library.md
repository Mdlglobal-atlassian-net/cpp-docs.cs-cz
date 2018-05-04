---
title: Správa knihovny | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
dev_langs:
- C++
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97c6da9e12e9071b4792476d2e49739a55d7ea8e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="managing-a-library"></a>Správa knihovny
K vytvoření nebo úpravě knihovnu COFF objektů, které je výchozí režim pro LIB. LIB běží v tomto režimu, když zadáte/extract (Chcete-li zkopírovat do souboru objektu) nebo/def (k vytvoření knihovnu importu).  
  
 Pokud chcete vytvořit knihovnu z objekty a knihovny, použijte následující syntaxi:  
  
```  
LIB [options...] files...  
```  
  
 Tento příkaz vytvoří knihovnu z jednoho nebo více vstup *soubory*. *Soubory* mohou být soubory COFF objektu, 32bitové OMF – soubory objektů nebo existující knihoven COFF. LIB vytvoří jedna knihovna, která obsahuje všechny objekty v zadané soubory. Pokud vstupní soubor je soubor 32-bit OMF objektu, bude v LIB převede do COFF před vytvořením knihovny. LIB nelze přijmout objekt OMF 32-bit, který je uložený v knihovně vytvořená 16bitové verzi LIB. Je nutné nejprve použít LIB 16bitové extrahovat objekt; pak můžete soubor odděleného objektu jako vstup pro 32-bit LIB.  
  
 Ve výchozím nastavení, LIB názvy výstupního souboru použitím základní název první soubor objekt nebo knihovny a rozšíření. lib. Výstupní soubor zprovozněn v aktuálním adresáři. Pokud soubor se stejným názvem již existuje, výstupní soubor nahradí existující soubor. Pokud chcete zachovat existující knihovnu, pomocí možnosti/out můžete zadat název souboru výstupního souboru.  
  
 K vytváření a úprava knihovnu použít následující možnosti:  
  
 / LIBPATH: `dir`  
 Přepíše danou cestu knihovny prostředí. Podrobnosti najdete v tématu Popis odkazu [/Libpath](../../build/reference/libpath-additional-libpath.md) možnost.  
  
 NEBO JEJICH VÝPISU  
 Zobrazí informace o knihovně výstup standardním výstupu. Výstup můžete přesměrovat do souboru. / List můžete použít k určení obsahu existující knihovny bez provádění úprav.  
  
 / NAME: *filename*  
 Při sestavování knihovnu importu, určuje název knihovny DLL, pro kterou je vytvořený knihovny importu.  
  
 / NODEFAULTLIB  
 Odebere ze seznamu knihoven, které vyhledávání při rozpoznávání externí odkazy na jeden nebo více výchozí knihovny. V tématu [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) Další informace.  
  
 / OUT: *filename*  
 Přepíše výchozí název výstupního souboru. Ve výchozím nastavení, vytvoření knihovny výstup v aktuálním adresáři s základní název první knihovny nebo objekt soubor na příkazovém řádku a rozšíření. lib.  
  
 Nebo odebrat: *objektu*  
 Vynechá zadaný *objekt* z knihovny výstup. LIB vytvoří výstupní knihovny kombinování všechny objekty (ať už v objektu soubory nebo knihovny) a pak odstranění objektů zadaným/remove.  
  
 / SUBSYSTEM: {KONZOLY &AMP;#124; EFI_APPLICATION &AMP;#124; EFI_BOOT_SERVICE_DRIVER &AMP;#124; EFI_ROM &AMP;#124; EFI_RUNTIME_DRIVER &AMP;#124; NATIVNÍ &AMP;#124; POSIX &AMP;#124; WINDOWS &AMP;#124; WINDOWSCE} [, #[. ##]]  
 Informuje operačního systému, jak spustit program vytvořené připojování ke knihovně výstup. Další informace najdete v tématu Popis odkazu [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) možnost.  
  
 Možnosti LIB zadat na příkazovém řádku se nerozlišují malá a velká písmena.  
  
 LIB můžete provádět následující úlohy správy knihovny:  
  
-   Chcete-li přidat objekty do knihovny, zadejte název souboru pro existující knihovnu a názvy souborů pro všechny nové objekty.  
  
-   Kombinování knihovny, zadejte názvy souborů knihovny. Můžete přidat objekty a kombinovat knihovny jedním příkazem LIB.  
  
-   Pokud chcete nahradit člena knihovny nový objekt, zadejte název souboru pro nový objekt (nebo knihovnu, která obsahuje ho) a knihovna, která obsahuje objekt člena, který chcete nahradit. Když v více než jeden vstupní soubor existuje objekt, který má stejný název, uloží je LIB poslední objekt zadaný v příkazu LIB do knihovny výstup. Když nahradíte člena knihovny, je nutné zadat nový objekt nebo knihovny po knihovnu, která obsahuje původní objekt.  
  
-   Pokud chcete odstranit člena z knihovny, použijte možnost/Remove. LIB zpracovává všechny specifikace/Remove po kombinování všechny vstupní objekty, bez ohledu na příkazový řádek pořadí.  
  
> [!NOTE]
>  Nelze jak odstranit členem a rozbalte ho do souboru do jednoho kroku. Nejdřív musíte extrahovat objektem člena pomocí/extract a potom spusťte LIB znovu s použitím/remove. Toto chování se liší od 16bitové LIB (pro knihovny OMF) uvedené v další produkty společnosti Microsoft.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)