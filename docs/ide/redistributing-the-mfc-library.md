---
title: Redistribuce knihovny MFC | Dokumentace Microsoftu
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
ms.openlocfilehash: 6e23358e17558c436d82a3226f84c35a59bf63a1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691213"
---
# <a name="redistributing-the-mfc-library"></a>Redistribuce knihovny MFC
Pokud dynamicky propojíte aplikaci ke knihovně MFC, musíte redistribuovat odpovídající knihovny MFC DLL. Například pokud aplikace knihovny MFC je vytvořená pomocí verze knihovny MFC, která se dodává s Visual Studiem 2015, musíte redistribuovat mfc140.dll nebo mfc140u.dll, v závislosti na tom, zda vaše aplikace je kompilován pro úzkých znaků nebo podpora kódování Unicode.  
  
> [!NOTE]
>  Soubory mfc140.dll byly vynechány z adresáře distribuovatelné soubory v sadě Visual Studio 2015 RTM. Můžete použít verze Visual Studio 2015 v adresářích Windows\system32 a Windows\syswow64 místo toho nainstaluje.  
  
 Protože všechny knihovny DLL MFC používají sdílenou verzi knihovny runtime jazyka C (CRT), budete také muset distribuovat CRT. Verze knihovny MFC, která se dodává s Visual Studiem 2015 používá universal CRT knihovny, který je distribuován jako součást systému Windows 10. Ke spuštění aplikace knihovny MFC sestavené pomocí sady Visual Studio 2015 ve starších verzích Windows, je třeba znovu distribuovat na Universal CRT. Informace o tom, jak znovu distribuovat na universal CRT jako součást operačního systému nebo pomocí místních nasazení, najdete v části [Představujeme Universal CRT](http://go.microsoft.com/fwlink/p/?linkid=617977). Chcete-li stáhnout univerzální CRT pro centrální nasazení o podporovaných verzích Windows, naleznete v tématu [Windows 10 Universal C Runtime](http://go.microsoft.com/fwlink/p/?LinkId=619489). V sadě Windows SDK se našly Redistributable verze specifické pro architekturu ucrtbase.dll pro místní nasazení. Ve výchozím nastavení Visual Studio nainstaluje do C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ specifické pro architekturu podadresáře.  
  
 Pokud jste aplikaci vytvořili pomocí starší verze knihovny MFC, musíte redistribuovat odpovídající CRT knihovny DLL z adresáře redistribuovatelné soubory. Například pokud vaše aplikace knihovny MFC je sestavena pomocí sady nástrojů Visual Studio 2013 (vc120), je třeba znovu distribuovat msvcr120.dll. Je také nutné znovu distribuovat odpovídající mfc`<version>`u.dll nebo mfc`<version>`.dll.  
  
 Pokud staticky propojíte aplikaci ke knihovně MFC (tj. Pokud zadáte **použít knihovnu MFC ve statické knihovně** na **Obecné** kartu **stránky vlastností** dialogové okno), není nutné Redistribuce knihovny MFC DLL. Nicméně i když statické propojení může fungovat pro testování a vnitřní nasazení aplikací, doporučujeme vám, že je velmi riskantní používat ji k redistribuci knihovny MFC. Další informace o doporučených strategiích nasazení knihoven Visual C++, naleznete v tématu [volba metody nasazení](../ide/choosing-a-deployment-method.md).  
  
 Pokud vaše aplikace používá třídy knihovny MFC implementující ovládací prvek WebBrowser (například [CHtmlView – třída](../mfc/reference/chtmlview-class.md) nebo [CHtmlEditView – třída](../mfc/reference/chtmleditview-class.md)), doporučujeme také nainstalovat nejnovější verzi Microsoft Internet Explorer tak, aby cílový počítač obsahoval nejaktuálnější soubory obvyklých ovládacích prvků. (Minimálně je vyžadována aplikace Internet Explorer 4.0.) Informace o instalaci komponent aplikace Internet Explorer je k dispozici v "Článku 185375: jak na vytvoření jedné EXE instalace aplikace Internet Explorer" na webu Microsoft Support.  
  
 Pokud vaše aplikace používá databázové třídy MFC (například [CRecordset – třída](../mfc/reference/crecordset-class.md) a [CRecordView – třída](../mfc/reference/crecordview-class.md)), musíte redistribuovat rozhraní ODBC a všechny ovladače rozhraní ODBC, které vaše aplikace používá.  
  
 Pokud vaše aplikace knihovny MFC používá ovládací prvky Windows Forms, musíte redistribuovat mfcmifc80.dll s vaší aplikací. Tato knihovna DLL je silný název podepsané sestavení .NET, které lze redistribuovat v místní složce aplikace nebo jejím zavedením do globální mezipaměti sestavení (GAC) pomocí aplikace [Gacutil.exe (Global Assembly Cache Tool)](/dotnet/framework/tools/gacutil-exe-gac-tool).  
  
 Pokud redistribuujete knihovny MFC DLL, ujistěte se, že redistribuujete prodejní verzi a ne ladicí verzi. Ladicí verze knihoven DLL nejsou redistribuovatelné. Názvy ladicích verzí knihoven MFC DLL končí písmenem "d", například Mfc140d.dll.  
  
 Můžete redistribuovat knihovnu MFC pomocí VCRedist_*architektura*.exe, slučovacích modulů, které jsou nainstalované s Visual Studio nebo nasazením knihovny MFC DLL do stejné složky jako vaši aplikaci. Další informace o redistribuci MFC naleznete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="installation-of-localized-mfc-components"></a>Instalace lokalizovaných komponent knihovny MFC  
 Pokud se rozhodnete lokalizovat aplikaci instalací lokalizační knihovny DLL MFC, musíte použít redistribuovatelné soubory sloučení (MSM). Například, pokud chcete lokalizovat vaši aplikaci v x x86 počítače, musíte sloučit Microsoft_VC`<version>`_MFCLOC_x86.msm do instalačního balíčku pro x x86 počítače.  
  
 Redistribuovatelné soubory MSM obsahují knihovny DLL, které se používají pro lokalizaci. Existuje jedna knihovna DLL pro každý podporovaný jazyk. Proces instalace nainstalujte tyto knihovny DLL do složky %windir%\system32\ v cílovém počítači.  
  
 Další informace o tom, jak lokalizaci aplikací knihovny MFC naleznete v tématu [TN057: lokalizace komponent MFC](../mfc/tn057-localization-of-mfc-components.md).
  
 Můžete redistribuovat lokalizační knihovny MFC nasazením knihovny MFC DLL v lokální složce vaší aplikace. Další informace o způsobu redistribuci knihoven Visual C++, naleznete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)
