---
title: Redistribuce knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: 7b38299bc39ce282769e40e915847b2220ec28ca
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965612"
---
# <a name="redistributing-the-mfc-library"></a>Redistribuce knihovny MFC

Pokud dynamicky propojíte aplikaci s knihovnou MFC, je nutné znovu distribuovat vyhovující knihovny MFC DLL. Například pokud je vaše aplikace MFC sestavena pomocí verze knihovny MFC, která je dodávána se sadou Visual Studio 2015, je nutné znovu distribuovat mfc140. dll nebo mfc140u. dll v závislosti na tom, zda je aplikace kompilována s úzkými znaky nebo podporou kódování Unicode.

> [!NOTE]
>  Soubory mfc140. dll byly vynechány v adresáři redistribuovatelných souborů v aplikaci Visual Studio 2015 RTM. Místo toho můžete použít verze nainstalované v rámci sady Visual Studio 2015 v adresářích Windows\System32 a Windows\syswow64.

Vzhledem k tomu, že všechny knihovny MFC DLL používají sdílenou verzi běhové knihovny jazyka C (CRT), může být také nutné znovu distribuovat CRT. Verze knihovny MFC, která je dodávána se sadou Visual Studio 2015, používá univerzální knihovnu CRT, která je distribuována jako součást systému Windows 10. Chcete-li spustit aplikaci knihovny MFC sestavenou pomocí sady Visual Studio 2015 v dřívějších verzích systému Windows, je nutné znovu distribuovat Universal CRT. Informace o tom, jak redistribuovat Universal CRT jako součást operačního systému nebo pomocí místního nasazení, najdete v tématu [Představujeme Universal CRT](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/). Pokud si chcete stáhnout Universal CRT pro centrální nasazení v podporovaných verzích Windows, přečtěte si téma [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234). Verze ucrtbase. dll pro místní nasazení, které jsou specifické pro architekturu, najdete v Windows SDK. Ve výchozím nastavení Visual Studio nainstaluje tyto soubory v adresáři C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ do podadresáře specifického pro architekturu.

Pokud je vaše aplikace sestavena pomocí starší verze knihovny MFC, je nutné znovu distribuovat vyhovující knihovny CRT DLL z adresáře redistribuovatelných souborů. Například pokud je vaše aplikace MFC sestavena pomocí sady nástrojů Visual Studio 2013 (vc120), je nutné znovu distribuovat msvcr120. dll. Také je nutné znovu distribuovat vyhovující knihovny MFC`<version>`u. dll nebo knihovny MFC`<version>`. dll.

Pokud staticky propojíte aplikaci s knihovnou MFC (tj. Pokud zadáte **použít knihovnu MFC ve statické knihovně** na kartě **Obecné** v dialogovém okně **stránky vlastností** ), nemusíte znovu distribuovat knihovnu MFC DLL. I když statické propojení může fungovat pro testování a interní nasazení aplikací, doporučujeme, abyste ho nepoužívali k redistribuci knihovny MFC. Další informace o doporučených strategiích pro nasazení vizuálních C++ knihoven najdete v tématu [Volba metody nasazení](choosing-a-deployment-method.md).

Pokud vaše aplikace používá třídy MFC, které implementují ovládací prvek WebBrowser (například třída [CHtmlView –](../mfc/reference/chtmlview-class.md) nebo [CHtmlEditView](../mfc/reference/chtmleditview-class.md)), doporučujeme také nainstalovat nejaktuálnější verzi aplikace Microsoft Internet Explorer, aby cílový počítač měl nejaktuálnější soubory běžných ovládacích prvků. (Vyžaduje se minimálně Internet Explorer 4,0.) Informace o tom, jak nainstalovat součásti aplikace Internet Explorer, jsou k dispozici v článku 185375: jak vytvořit instalaci aplikace Internet Explorer s jedním EXE na webu podpora Microsoftu.

Pokud vaše aplikace používá databázové třídy knihovny MFC (například třída [CRecordset](../mfc/reference/crecordset-class.md) a [Třída CRecordView](../mfc/reference/crecordview-class.md)), je nutné znovu distribuovat rozhraní ODBC a všechny ovladače rozhraní ODBC, které vaše aplikace používá.

Pokud vaše aplikace MFC používá ovládací prvky model Windows Forms, je nutné znovu distribuovat mfcmifc80. dll s vaší aplikací. Tato knihovna DLL je podepsané sestavení .NET se silným názvem, které lze distribuovat pomocí aplikace v místní složce aplikace nebo jejich nasazením do globální mezipaměti sestavení (GAC) pomocí nástroje [Gacutil. exe (nástroj Global Assembly Cache Tool)](/dotnet/framework/tools/gacutil-exe-gac-tool).

Pokud redistribuujete knihovnu MFC DLL, nezapomeňte znovu distribuovat prodejní verzi, a ne ladicí verzi. Ladicí verze knihoven DLL nejsou distribuovatelné. Názvy ladicích verzí knihoven MFC DLL končí znakem "d", například Mfc140d. dll.

Knihovnu MFC lze znovu distribuovat pomocí VCRedist_*architektury*. exe, slučovacích modulů, které jsou nainstalovány se sadou Visual Studio, nebo nasazením knihovny MFC DLL do stejné složky jako vaše aplikace. Další informace o redistribuci knihovny MFC naleznete v tématu [Redistribuce vizuálních C++ souborů](redistributing-visual-cpp-files.md).

## <a name="installation-of-localized-mfc-components"></a>Instalace lokalizovaných komponent knihovny MFC

Pokud se rozhodnete lokalizovat aplikaci instalací knihovny DLL lokalizace knihovny MFC, je nutné použít redistribuovatelné soubory sloučení (. msm). Například pokud chcete, aby aplikace byla lokalizována v počítači x86, je nutné sloučit Microsoft_VC`<version>`_MFCLOC_x86. msm do instalačního balíčku pro počítač s architekturou x86.

Redistribuovatelné soubory. msm obsahují knihovny DLL, které se používají k lokalizaci. Pro každý podporovaný jazyk existuje jedna knihovna DLL. Proces instalace nainstaluje tyto knihovny DLL do složky%windir%\system32\ v cílovém počítači.

Další informace o lokalizaci aplikací knihovny MFC naleznete v tématu [TN057: LOCALIZATION MFC Components](../mfc/tn057-localization-of-mfc-components.md).

Knihovny DLL lokalizace knihovny MFC můžete znovu distribuovat nasazením knihovny MFC DLL do místní složky aplikace. Další informace o tom, jak znovu distribuovat vizuální C++ knihovny, naleznete v tématu [Redistribuce vizuálních C++ souborů](redistributing-visual-cpp-files.md).

## <a name="see-also"></a>Viz také:

[Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)
