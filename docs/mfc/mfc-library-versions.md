---
title: MFC – knihovní verze | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1781077896465d8a7a1d925262c3fd0696d24380
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410556"
---
# <a name="mfc-library-versions"></a>MFC – verze knihovny

Knihovna MFC je k dispozici ve verzích, které podporují ANSI jednobajtové a vícebajtové znakové sady (MBCS) kódu, jakož i verze, které podporují kódování Unicode (s kódováním UTF-16LE, znakové sady Windows native). Každá verze rozhraní MFC je k dispozici jako statické knihovny nebo sdílené knihovny DLL. Je také menší statické knihovní verze rozhraní MFC, která mimo MFC – ovládací prvky pro dialogová okna pro aplikace, které jsou velmi citlivé na velikost a nepotřebují tyto ovládací prvky. Knihovny MFC jsou k dispozici v obou ladění a vydání verze pro podporované architektury, které zahrnují x86 x64 a procesory ARM. Můžete vytvořit pro obě aplikace (soubory .exe) a knihovny DLL s jakoukoli verzi knihovny MFC. Existuje také sada knihoven MFC pro propojení se spravovaným kódem. Sdílené knihovny DLL MFC zahrnují číslo verze k označení binární kompatibilitu knihovny.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatické propojení knihovní verze knihovny MFC

Soubory hlaviček knihovny MFC automaticky určit správnou verzi knihovny MFC pro propojení, založený na hodnotách definovaných ve vašem prostředí sestavení. Soubory hlaviček knihovny MFC Přidání direktivy kompilátoru propojovací program na odkaz v konkrétní verzi knihovny MFC.

Například, afx –. Soubor hlaviček H přikáže linkeru odkaz v celý statický, omezené statické, nebo sdílené knihovny DLL verzi knihovny MFC; ANSI/znakové sady MBCS a Unicode verze; a ladění nebo maloobchodní verze, v závislosti na konfiguraci sestavení:

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

Soubory hlaviček knihovny MFC také obsahovat direktivy propojení ve všech požadovaných knihovnách včetně knihovny MFC, knihovny Win32, knihovny OLE, vytvořené z ukázek knihovny OLE, ODBC knihovny a tak dále.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, znakové sady MBCS a Unicode

Verze knihovny MFC standardu ANSI/MBCS podporují oba jednobajtový znak, jako je například ASCII a vícebajtové znakové sady například Shift-JIS. Verze knihovny MFC kódování Unicode podporu v podobě kódováním UTF-16LE širokého znaku Unicode. Použití verze knihovny ANSI/MBCS knihoven MFC pro podporu kódování Unicode kódování UTF-8.

K nastavení konfigurace projektu pro použití v integrovaném vývojovém prostředí jednobajtový vícebajtový nebo širokého znaku podporu řetězců a znaků Unicode, použijte **vlastnosti projektu** dialogového okna. V **vlastnosti konfigurace** > **Obecné** nastavte **znaková sada** vlastnost **Nenastaveno** používat jednobajtové znakové sadě. Nastavte vlastnost na **použít vícebajtovou znakovou sadu** vícebajtové znakové sady, nebo **pomocí Unicode znaková sada** používat jako UTF-16 kódování Unicode.

Projekty MFC používají symbol preprocesoru \_UNICODE označuje podporu širokého znaku Unicode UTF-16, a \_Podpora MBCS udávajících znakové sady MBCS. Tyto možnosti se vzájemně vylučují v projektu.

## <a name="mfc-static-library-naming-conventions"></a>Konvence pojmenování statické knihovny MFC

Statické knihovny MFC pomocí následující názvové konvence. Názvy knihoven mít formát _služba ._protokol

> *u*AFX*c**d*.LIB

zobrazí kurzívou malá písmena, kde jsou zástupné symboly specifikátory jehož význam, jsou uvedeny v následující tabulce:

|Specifikátor|Hodnoty a vysvětlení|
|---------------|-------------------------|
|*u*|ANSI/znakové sady MBCS (N) nebo Unicode (U); Vynechat pro verzi bez MFC – ovládací prvky v dialogových oknech|
|*c*|Verze s MFC – ovládací prvky v dialogových oknech (CW) nebo bez (NMCD)|
|*d*|Ladit nebo vydaná verze: D = Debug; vynechat specifikátor verze|

Všechny knihovny, které jsou uvedeny v následující tabulce jsou zahrnuty v adresáři \atlmfc\lib pro podporované sestavení architektury předem připravené.

|Knihovna|Popis|
|-------------|-----------------|
|NAFXCW.LIB|Staticky propojené knihovny MFC, prodejní verze|
|NAFXCWD.LIB|Staticky propojené knihovny MFC, ladicí verze|
|UAFXCW.LIB|Staticky propojené knihovny MFC s podporou kódování Unicode, prodejní verze|
|UAFXCWD.LIB|Staticky propojené knihovny MFC s podporou kódování Unicode, ladicí verze|
|AFXNMCD.LIB|Staticky propojené knihovny MFC bez ovládací prvky dialogového okna knihovny MFC, prodejní verze|
|AFXNMCDD.LIB|Staticky propojené knihovny MFC bez ovládací prvky dialogového okna knihovny MFC, ladicí verze|

Soubory ladicího programu, které mají stejný základní název a příponou PDB jsou také k dispozici pro každý statických knihoven.

## <a name="mfc-shared-dll-naming-conventions"></a>Sdílená knihovna MFC DLL zásady vytváření názvů

MFC sdílené knihovny DLL také následující zásady strukturovaného vytváření názvů. Díky tomu snadnější zjistit, které knihovny DLL nebo knihovny byste měli použít pro konkrétní účel.

Knihovny DLL MFC mají *verze* čísla označující binární kompatibilitu. Použití knihovny MFC DLL, které mají stejnou verzi jako vaší knihovny a sady nástrojů kompilátoru k zajištění kompatibility v rámci projektu.

|DLL|Popis|
|---------|-----------------|
|MFC*verze*. KNIHOVNY DLL|MFC DLL, ANSI nebo znakové sady MBCS vydání verze|
|MFC*version*U.DLL|Knihovny MFC DLL, Unicode verze|
|MFC*version*D.DLL|Verze knihovny MFC DLL, ANSI nebo ladění znakové sady MBCS|
|MFC*version*UD.DLL|Knihovny MFC DLL, Unicode ladicí verze|
|MFCM*verze*. KNIHOVNY DLL|MFC DLL pomocí ovládacích prvků Windows Forms, ANSI nebo znakové sady MBCS vydání verze|
|MFCM*verze*U.DLL|Pomocí ovládacích prvků Windows Forms, Unicode verze knihovny MFC DLL|
|MFCM*version*D.DLL|MFC DLL pomocí ovládacích prvků Windows Forms, verze ANSI nebo ladění znakové sady MBCS|
|MFCM*version*UD.DLL|Pomocí ovládacích prvků Windows Forms, Unicode ladicí verze knihovny MFC DLL|

Importovat knihovny potřebné k sestavení aplikace nebo MFC – rozšiřující knihovny DLL, které používají tyto sdílené knihovny DLL mají stejný základní název jako knihovna DLL, ale mají příponu názvu souboru LIB. Při použití sdílené knihovny DLL, malé statické knihovny musí být stále propojené s vaším kódem; Tato knihovna je s názvem MFCS*verze*lib {U} {D}.

Pokud jsou dynamického propojení ke sdílené knihovně DLL verze knihovny MFC, ať už z aplikace nebo rozšiřující knihovny DLL MFC, je nutné zahrnout odpovídající MFC*verze*. Knihovna DLL nebo knihovny MFC*verze*U.DLL při nasazování produktu.

Seznam knihoven DLL Visual C++, který se dá distribuovat s vašimi aplikacemi najdete v tématu [Distribuovatelný kód pro Microsoft Visual Studio 2017 a Microsoft Visual Studio 2017 SDK (zahrnuje soubory Buildovacího serveru a)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Další informace o podpoře znakové sady MBCS a Unicode v prostředí MFC, naleznete v tématu [vícebajtové znakové sady (MBCS) Podpora kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Podpora knihovny DLL

Můžete použít buď statická nebo sdílené dynamické knihovny MFC pro vytvoření DLL knihoven, které mohou být využívána spustitelné soubory knihovny MFC a non-MFC. Ty se nazývají "obvyklé knihovny DLL" nebo "obvyklé knihovny DLL MFC", abychom je odlišili od MFC – rozšiřující knihovny DLL, které mohou být pouze používané aplikace knihovny MFC a knihovny MFC DLL. Knihovny DLL vytvořené pomocí statické knihovny MFC se někdy označuje jako USRDLL starší odkazy, protože projekty knihovny MFC DLL, definujte symbol preprocesoru  **\_USRDLL**. Knihovny DLL, že používá MFC sdílené knihovny DLL se někdy nazývá AFXDLL starší odkazy, protože definuje symbol preprocesoru  **\_AFXDLL**.

Při vytváření projektu knihovny DLL odkazování na statické knihovny MFC, knihovny DLL se dá nasadit bez knihovny MFC sdílené knihovny DLL. Pokud váš projekt knihovny DLL odkazuje na importní knihovny MFC*verze*. LIB nebo MFC*verze*U.LIB, je nutné nasadit odpovídající sdílené knihovny MFC DLL MFC*verze*. Knihovna DLL nebo knihovny MFC*verze*U.DLL společně s vaší knihovny DLL. Další informace najdete v tématu [knihovny DLL](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Viz také:

[Obecná témata MFC](../mfc/general-mfc-topics.md)
