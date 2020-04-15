---
title: Redistribuce knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: e1434bee6d134d4c02b2c06125d340a68a6c305d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359907"
---
# <a name="redistributing-the-mfc-library"></a>Redistribuce knihovny MFC

Pokud dynamicky propojíte aplikaci s knihovnou knihovny MFC, je nutné znovu distribuovat odpovídající knihovnu DLL knihovny MFC. Pokud je například aplikace knihovny MFC vytvořena pomocí verze knihovny MFC, která je dodávána s Visual Studio 2015, musíte znovu distribuovat mfc140.dll nebo mfc140u.dll v závislosti na tom, jestli je vaše aplikace kompilovaná pro úzké znaky nebo podporu Unicode.

> [!NOTE]
> Soubory mfc140.dll byly vynechány z adresáře redistribuovatelných souborů v sadě Visual Studio 2015 RTM. Místo toho můžete použít verze nainstalované visual studio 2015 v adresářích Windows\system32 a Windows\syswow64.

Vzhledem k tomu, že všechny knihovny DLL knihovny MFC používají sdílenou verzi knihovny runtime C (CRT), může být také nutné znovu distribuovat CRT. Verze knihovny MFC, která je dodávána s Visual Studio 2015 používá univerzální knihovnu CRT, která je distribuována jako součást Windows 10. Chcete-li spustit aplikaci knihovny MFC vytvořenou pomocí sady Visual Studio 2015 v dřívějších verzích systému Windows, je nutné znovu distribuovat univerzální CRT. Informace o tom, jak redistribuovat univerzální CRT jako součást operačního systému nebo pomocí místního nasazení, naleznete [v tématu Zavedení univerzální crt](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/). Informace o stažení univerzálního crt pro centrální nasazení v podporovaných verzích systému Windows najdete v článku [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234). Redistribuovatelné verze souboru ucrtbase.dll pro místní nasazení jsou k dispozici v sadě Windows SDK. Ve výchozím nastavení je sada Visual Studio instaluje do c:\programových souborů (x86)\sady Windows Kit\10\Redist\ucrt\DLL\ v podadresáři specifickém pro architekturu.

Pokud je vaše aplikace vytvořená pomocí starší verze knihovny knihovny MFC, musíte znovu distribuovat odpovídající knihovnu CRT DLL z adresáře redistribuovatelných souborů. Pokud je například aplikace knihovny MFC vytvořena pomocí sady nástrojů Visual Studio 2013 (vc120), je nutné knihovnu msvcr120.dll znovu distribuovat. Musíte také přerozdělit odpovídající mfc`<version>`u.dll`<version>`nebo mfc .dll.

Pokud staticky propojíte aplikaci s knihovnou MFC (to znamená, že zadáte **použít knihovnu MFC ve statické knihovně** na kartě **Obecné** v dialogovém okně **Stránky vlastností),** není nutné znovu distribuovat knihovnu DLL knihovny MFC. I když statické propojení může fungovat pro testování a interní nasazení aplikací, doporučujeme nepoužívat k redistribuci knihovny MFC. Další informace o doporučených strategiích pro nasazení knihoven Visual C++ naleznete [v tématu Výběr metody nasazení](choosing-a-deployment-method.md).

Pokud vaše aplikace používá třídy knihovny MFC, které implementují ovládací prvek WebBrowser (například [CHtmlView Class](../mfc/reference/chtmlview-class.md) nebo [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)), doporučujeme také nainstalovat nejnovější verzi aplikace Microsoft Internet Explorer tak, aby cílový počítač měl nejaktuálnější běžné řídicí soubory. (Je vyžadována minimálně aplikace Internet Explorer 4.0.) Informace o instalaci součástí aplikace Internet Explorer jsou k dispozici v článku 185375: Jak vytvořit jednu instalaci aplikace Internet Explorer exe na webu podpory společnosti Microsoft.

Pokud vaše aplikace používá třídy databáze knihovny MFC (například [CRecordset Class](../mfc/reference/crecordset-class.md) a [CRecordView Class](../mfc/reference/crecordview-class.md)), je nutné znovu distribuovat rozhraní ODBC a všechny ovladače ODBC, které aplikace používá.

Pokud aplikace Knihovny MFC používá ovládací prvky Windows Forms, je nutné redistribuovat soubor mfcmifc80.dll s vaší aplikací. Tato dll je sestavení .NET podepsané silným názvem, které lze znovu distribuovat s aplikací v místní složce aplikace nebo jejím nasazením do globální mezipaměti sestavení (GAC) pomocí [nástroje Gacutil.exe (Global Assembly Cache Tool).](/dotnet/framework/tools/gacutil-exe-gac-tool)

Pokud redistribuujete knihovnu DLL knihovny MFC, ujistěte se, že redistribuujete maloobchodní verzi a ne ladicí verzi. Ladicí verze knihoven DLL nelze znovu distribuovat. Názvy ladicích verzí knihovny DLL knihovny MFC končí knihovnou DLL "d", například Mfc140d.dll.

Knihovny MFC můžete dále distribuovat pomocí VCRedist_*architektury*.exe, slučovacích modulů nainstalovaných v sadě Visual Studio nebo nasazením knihovny MFC DLL do stejné složky jako aplikace. Další informace o tom, jak znovu distribuovat knihovnu MFC, naleznete [v tématu Redistributing Visual C++ Files](redistributing-visual-cpp-files.md).

## <a name="installation-of-localized-mfc-components"></a>Instalace lokalizovaných součástí knihovny MFC

Pokud se rozhodnete lokalizovat aplikaci instalací knihovny DLL lokalizace knihovny MFC, musíte použít redistribuovatelné soubory sloučení (.msm). Chcete-li například lokalizovat aplikaci v počítači x86,`<version>`je nutné sloučit Microsoft_VC _MFCLOC_x86.msm do instalačního balíčku pro počítač x86.

Redistribuovatelné soubory MSM obsahují knihovny DLL, které se používají pro lokalizaci. Pro každý podporovaný jazyk existuje jedna dll. Instalační proces nainstaluje tyto knihovny DLL do složky %windir%\system32\ v cílovém počítači.

Další informace o lokalizaci aplikací knihovny MFC naleznete v [tématu TN057: Lokalizace součástí knihovny MFC](../mfc/tn057-localization-of-mfc-components.md).

Knihovny DLL lozitizace knihovny MFC můžete dále distribuovat nasazením knihovny DLL knihovny MFC v místní složce aplikace. Další informace o tom, jak redistribuovat knihovny visual c++, naleznete [v tématu Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md).

## <a name="see-also"></a>Viz také

[Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)
