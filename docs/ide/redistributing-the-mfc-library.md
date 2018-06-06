---
title: Redistribuce knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a49bf18721f605abe0c6e496d3532012c9c92c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340395"
---
# <a name="redistributing-the-mfc-library"></a>Redistribuce knihovny MFC
Pokud jste dynamicky aplikace knihovny MFC, je třeba znovu distribuovat odpovídající MFC DLL. Například pokud aplikace MFC je integrovaný s použitím verze knihovny MFC, který se dodává s Visual Studiem 2015, je třeba znovu distribuovat mfc140.dll nebo mfc140u.dll, v závislosti na tom, jestli je vaše aplikace zkompilovaném pro úzké znaků nebo podpora kódování Unicode.  
  
> [!NOTE]
>  Soubory mfc140.dll byly vynechány z adresáře redistribuovatelné soubory ve Visual Studio 2015 RTM. Verze nainstalované pomocí sady Visual Studio 2015 v adresáři Windows\system32 a Windows\syswow64 místo toho můžete použít.  
  
 Protože všechny knihovny MFC DLL používat sdílené verzi běhové knihovny jazyka C (CRT), může také muset znovu distribuovat CRT. Verze knihovny MFC, který se dodává s Visual Studiem 2015 používá universal CRT knihovny, která se distribuuje v rámci Windows 10. Pokud chcete spustit aplikaci MFC sestavené pomocí sady Visual Studio 2015 v dřívějších verzích systému Windows, je třeba znovu distribuovat Universal CRT. Informace o tom, jak znovu distribuovat universal CRT jako součást operačního systému nebo pomocí místní nasazení najdete v tématu [představení Universal CRT](http://go.microsoft.com/fwlink/p/?linkid=617977). Chcete-li stáhnout univerzální CRT pro centrální nasazení v podporovaných verzích systému Windows, přečtěte si téma [Windows 10 Universal C Runtime](http://go.microsoft.com/fwlink/p/?LinkId=619489). Ve Windows SDK se našly Redistributable verze specifické pro architekturu ucrtbase.dll pro místní nasazení. Ve výchozím nastavení nainstaluje Visual Studio v C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ v konkrétní architektury podadresář.  
  
 Pokud vaše aplikace je vytvořené pomocí dřívější verze knihovny MFC, je třeba znovu distribuovat odpovídající CRT knihovny DLL z adresáře redistribuovatelné soubory. Například pokud vaše aplikace knihovny MFC je sestaven pomocí nástrojů Visual Studio 2013 (vc120), je třeba znovu distribuovat msvcr120.dll. Je také nutné znovu distribuovat odpovídající mfc`<version>`u.dll nebo mfc`<version>`.dll.  
  
 Pokud jste staticky aplikace MFC (tj. Pokud zadáte **MFC použití statické knihovny** na **Obecné** ve **stránky vlastností** dialogové okno), nemáte Redistribuce knihovny MFC DLL. Nicméně Přestože statické propojení může fungovat pro testování a interní nasazení aplikací, doporučujeme používat ji Redistribuce knihovny MFC. Další informace o doporučených strategie pro nasazení knihovny jazyka Visual C++, najdete v části [volba metody nasazení](../ide/choosing-a-deployment-method.md).  
  
 Pokud vaše aplikace používá knihovny MFC třídy, které implementují ovládacího prvku WebBrowser (například [CHtmlView třída](../mfc/reference/chtmlview-class.md) nebo [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)), doporučujeme také nainstalovat nejnovější verzi Aplikace Microsoft Internet Explorer tak, aby měla nejaktuálnější společné soubory řízení cílový počítač. (Minimálně, je vyžadována aplikace Internet Explorer 4.0.) Informace o tom, jak nainstalovat součástí aplikace Internet Explorer je k dispozici v "Článek 185375: jak k vytvoření jeden EXE instalace v aplikaci Internet Explorer" na webu Microsoft Support.  
  
 Pokud vaše aplikace používá třídami databází MFC (například [CRecordset – třída](../mfc/reference/crecordset-class.md) a [CRecordView – třída](../mfc/reference/crecordview-class.md)), je třeba znovu distribuovat rozhraní ODBC a všechny ovladače ODBC, které vaše aplikace používá. Další informace najdete v tématu [Redistribuce pomocných souborů databáze](../ide/redistributing-database-support-files.md).  
  
 Pokud vaše aplikace knihovny MFC používá ovládací prvky Windows Forms, je třeba znovu distribuovat mfcmifc80.dll s vaší aplikací. Tuto knihovnu DLL se silným názvem podepsané sestavení rozhraní .NET, které můžete distribuovat pomocí aplikace v jeho místní složky nebo po jeho nasazení do globální mezipaměti sestavení (GAC) pomocí [Gacutil.exe (Global Assembly Cache Tool)](/dotnet/framework/tools/gacutil-exe-gac-tool).  
  
 Pokud je znovu distribuovat knihovně MFC DLL, ujistěte se, že jste znovu distribuovat na prodejní verzi a ne ladicí verzi. Ladicí verze knihoven DLL nejsou redistributable. Názvy ladicí verze knihovny MFC DLL končit "d", například Mfc140d.dll.  
  
 Je možné znovu distribuovat MFC pomocí buď VCRedist_*architektura*.exe, slučovacích modulů, které jsou nainstalované s Visual Studio, nebo nasazení MFC DLL do stejné složky jako aplikace. Další informace o tom, jak znovu distribuovat MFC najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="installation-of-localized-mfc-components"></a>Instalace lokalizovaných komponent knihovny MFC  
 Pokud se rozhodnete k lokalizaci aplikace nainstalováním lokalizace MFC DLL, musíte použít soubory redistributable sloučení (MSM). Například, pokud chcete lokalizovat vaší aplikace na x86 počítače, musíte sloučit Microsoft_VC`<version>`_MFCLOC_x86.msm do instalačního balíčku pro x86 počítače.  
  
 Soubory distribuovatelného .msm obsahují knihovny DLL, které se používají pro lokalizaci. Neexistuje jeden knihovny DLL pro každý podporovaný jazyk. Proces instalace nainstaluje tyto knihovny DLL ve složce %windir%\system32\ na cílovém počítači.  
  
 Další informace o tom, jak lokalizace aplikací MFC najdete v tématu [TN057: lokalizace komponent MFC](../mfc/tn057-localization-of-mfc-components.md)a také [208983 článek: postup pomocí knihovny MFC DLL umístění](http://go.microsoft.com/fwlink/p/?linkid=198025) na webu Microsoft Support.  
  
 Lokalizace MFC – knihovny DLL je možné znovu distribuovat nasazením knihovně MFC DLL v místní složce aplikace. Další informace o tom, jak znovu distribuovat knihovny jazyka Visual C++ najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)