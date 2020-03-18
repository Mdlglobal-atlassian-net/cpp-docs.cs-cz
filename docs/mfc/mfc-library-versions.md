---
title: MFC – verze knihovny
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420174"
---
# <a name="mfc-library-versions"></a>MFC – verze knihovny

Knihovna MFC je dostupná ve verzích, které podporují jednobajtové znakové sady ANSI a vícebajtové znakové sady (MBCS) a také verze podporující kódování Unicode (kódované jako UTF-16LE, sada znaků nativní pro systém Windows). Každá verze knihovny MFC je k dispozici jako Statická knihovna nebo jako sdílená knihovna DLL. Existuje také menší verze statické knihovny knihovny MFC, která opustí ovládací prvky MFC pro dialogy pro aplikace, které jsou velmi citlivé na velikost a nepotřebují tyto ovládací prvky. Knihovny MFC jsou k dispozici v ladicí i prodejní verzi pro podporované architektury, které zahrnují procesory x86, x64 a ARM. Můžete vytvořit obě aplikace (soubory. exe) a knihovny DLL s libovolnou verzí knihoven MFC. K dispozici je také sada knihoven MFC kompilovaných pro propojení se spravovaným kódem. Sdílené knihovny MFC Shared obsahují číslo verze pro označení binární kompatibility knihovny.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatické propojování verzí knihoven MFC

Soubory hlaviček knihovny MFC automaticky určují správnou verzi knihovny MFC, která se má propojit, na základě hodnot definovaných ve vašem prostředí sestavení. Soubory hlaviček knihovny MFC přidávají direktivy kompilátoru, které řídí linker, aby propojí v konkrétní verzi knihovny MFC.

Například AFX –. Soubor hlaviček H instruuje linker, aby propojí v plné statické, omezené statické nebo sdílené knihovně DLL verze MFC; ANSI/MBCS nebo verze Unicode; a ladění nebo prodejní verze v závislosti na konfiguraci sestavení:

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

Soubory hlaviček knihovny MFC také obsahují direktivy pro propojení ve všech požadovaných knihovnách, včetně knihoven MFC, knihoven Win32, knihoven OLE, knihoven OLE vytvořených ze vzorků, knihoven ODBC a tak dále.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS a Unicode

Verze knihovny MFC ANSI/MBCS podporuje dvoubajtové znakové sady, jako je například ASCII, a vícebajtové znakové sady, jako je například Shift-JIS. Verze knihovny MFC Unicode podporuje Unicode ve formátu UTF-16LE s kódováním znaků. Pro podporu kódování Unicode UTF-8 použijte verzi knihovny ANSI/MBCS.

Chcete-li nastavit konfiguraci projektu tak, aby v integrovaném vývojovém prostředí používala jednobajtové, vícebajtové nebo roztažitelné řetězce Unicode a podporu znaků, použijte dialogové okno **Vlastnosti projektu** . Na stránce **Vlastnosti konfigurace** > **Obecné** nastavte vlastnost **znaková sada** na hodnotu **Nenastaveno** na použít jednobajtové znakové sady. Nastavte vlastnost na použití vícebajtové znakové **sady** pro použití vícebajtové znakové sady nebo pro použití **znakové sady Unicode** s kódováním Unicode UTF-16.

Projekty MFC používají symbol preprocesoru \_UNICODE k označení podpory znakové sady UTF-16 pro velké písmeno a \_znakové sady MBCS k označení podpory znakové sady MBCS. Tyto možnosti se vzájemně vylučují v projektu.

## <a name="mfc-static-library-naming-conventions"></a>Konvence pojmenování statických knihoven MFC

Statické knihovny pro MFC používají následující konvence pojmenování. Názvy knihoven mají tvar

> <em>u</em> AFX –<em>CD</em>. Knihovna

kde písmena zobrazená kurzívou jsou zástupné symboly pro specifikátory, jejichž význam je uveden v následující tabulce:

|Specifikátor|Hodnoty a významy|
|---------------|-------------------------|
|*h*|ANSI/MBCS (N) nebo Unicode (U); vynechat pro verzi bez ovládacích prvků MFC v dialogových oknech|
|*r*|Verze s ovládacími prvky MFC v dialozích (SH) nebo bez (NMCD)|
|*trojrozměrné*|Ladění nebo verze: D = ladění; vynechat specifikátor pro vydanou verzi|

Všechny knihovny, které jsou uvedeny v následující tabulce, jsou zahrnuty předem v adresáři \atlmfc\lib pro podporované architektury sestavení.

|Knihovna|Popis|
|-------------|-----------------|
|NAFXCW.LIB|Statická knihovna MFC, verze pro vydání|
|NAFXCWD.LIB|Statická knihovna MFC, ladicí verze|
|UAFXCW.LIB|Statická knihovna MFC s podporou kódování Unicode, verze vydaná pro vydání|
|UAFXCWD.LIB|Statická knihovna MFC s podporou kódování Unicode, ladicí verze|
|AFXNMCD.LIB|Statická knihovna MFC bez ovládacích prvků dialogového okna MFC, verze vydaná pro vydání|
|AFXNMCDD.LIB|Statická knihovna MFC bez ovládacích prvků dialogového okna MFC, ladicí verze|

Soubory ladicího programu, které mají stejný základní název a příponu PDB, jsou k dispozici také pro každou ze statických knihoven.

## <a name="mfc-shared-dll-naming-conventions"></a>Konvence pojmenování sdílených knihoven DLL MFC

Sdílené knihovny DLL MFC také následují jako strukturované konvence vytváření názvů. Díky tomu je snazší zjistit, které knihovny DLL nebo knihovny byste měli používat pro tento účel.

Knihovny MFC DLL mají čísla *verzí* , která označují binární kompatibilitu. Používejte knihovny MFC DLL, které mají stejnou verzi jako vaše jiné knihovny a sady nástrojů kompilátoru pro zajištění kompatibility v rámci projektu.

|DLL|Popis|
|---------|-----------------|
|*Verze*knihovny MFC. DLL|MFC DLL, verze ANSI nebo verze znakové sady MBCS|
|MFC*verze*U. dll|MFC DLL, verze pro verzi Unicode|
|MFC*verze*D. dll|MFC DLL, ANSI nebo verze ladění znakové sady MBCS|
|UD*verze*knihovny MFC. DLL|MFC DLL, verze ladění Unicode|
|*Verze*MFCM DLL|MFC DLL s ovládacími prvky model Windows Forms, verzí verze ANSI nebo MBCS|
|MFCM*verze*U. dll|MFC DLL s ovládacími prvky model Windows Forms, verze Release Unicode|
|MFCM*verze*D. dll|MFC DLL s ovládacími prvky model Windows Forms, verze ladění ANSI nebo MBCS|
|MFCM*verze*ud. DLL|MFC DLL s ovládacími prvky model Windows Forms, ladicí verzí Unicode|

Knihovny importů potřebné pro sestavování aplikací nebo knihoven DLL rozšíření MFC, které používají tyto sdílené knihovny DLL, mají stejný základní název jako knihovna DLL, ale mají příponu názvu souboru. lib. Při použití sdílených knihoven DLL musí být stále propojena malá Statická knihovna s vaším kódem; Tato knihovna má název MFCS*verze*{U} {D}. lib.

Pokud dynamicky propojujete se sdílenou knihovnou DLL verze knihovny MFC, ať už je z aplikace, nebo z knihovny DLL rozšíření MFC, je nutné zahrnout vyhovující*verzi*knihovny MFC. Knihovna DLL nebo knihovna MFC*verze*U. dll při nasazení produktu.

Seznam vizuálních C++ knihoven DLL, které lze distribuovat s vašimi aplikacemi, naleznete v tématu [distribuovatelný kód pro Microsoft Visual Studio 2017 a Microsoft Visual Studio 2017 SDK (zahrnuje nástroje a soubory Buildovacího serveru)](/visualstudio/productinfo/2017-redistribution-vs) nebo [distribuovatelný kód pro Visual Studio 2019](/visualstudio/releases/2019/redistribution).

Další informace o podpoře znakové sady MBCS a Unicode v knihovně MFC naleznete v tématu [Podpora sady Unicode a vícebajtové znakové sady (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Podpora knihovny Dynamic-Link

Můžete použít statickou nebo sdílenou dynamickou knihovnu MFC k vytvoření knihoven DLL, které mohou být používány spustitelnými soubory MFC i non-MFC. Jsou označovány jako "běžné knihovny DLL" nebo "běžné knihovny MFC DLL", aby je bylo možné odlišit od rozšiřujících knihoven DLL MFC, které mohou používat pouze aplikace MFC a knihovny MFC DLL. Knihovna DLL sestavená pomocí statických knihoven knihovny MFC je někdy označována jako USRDLL ve starších odkazech, protože projekty knihovny MFC DLL definují symbol preprocesoru **\_USRDLL**. Knihovna DLL, která používá sdílené knihovny MFC, se někdy označuje jako AFXDLL – ve starších odkazech, protože definuje symbol preprocesoru **\_AFXDLL –** .

Při vytváření projektu knihovny DLL pomocí propojení ke statickým knihovnám knihovny MFC může být vaše knihovna DLL nasazena bez sdílených knihoven DLL knihovny MFC. Když projekt knihovny DLL odkazuje na*verzi*knihovny MFC pro import knihoven. LIB nebo MFC*verze*U. lib, musíte nasadit vyhovující*verzi*MFC Shared DLL MFC. DLL nebo knihovna MFC*verze*U. dll společně s vaší knihovnou DLL. Další informace najdete v tématu [knihovny DLL](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)
