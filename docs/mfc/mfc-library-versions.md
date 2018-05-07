---
title: MFC – verze knihovny | Microsoft Docs
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
ms.openlocfilehash: 9fb4f73d1a0360ddad3983179415d0f7fc2d3cda
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-library-versions"></a>MFC – verze knihovny

Knihovny MFC je k dispozici ve verzích, které podporují ANSI jednobajtové a vícebajtové znaková sada (MBCS) kód, jakož i verze, které podporují kódování Unicode (kódovaná jako znakové sady UTF-16LE, znaková sada Windows nativní). Každá verze knihovny MFC je k dispozici jako statické knihovny nebo sdílenou knihovnu DLL. Je také menší statické knihovní verze rozhraní MFC, který vynechány MFC – ovládací prvky pro dialogová okna pro aplikace, které jsou velmi citlivé na velikost a nepotřebujete tyto ovládací prvky. Knihovny MFC jsou k dispozici v obou ladění a vydání verze pro podporované architektury, které zahrnují x86, x64 a procesory ARM. Můžete vytvořit pro obě aplikace (soubory .exe) a všechny verze knihovny MFC – knihovny DLL. Je také sadu knihovny MFC zkompilovaném pro rozhraní k spravovaného kódu. MFC sdílené knihovny DLL obsahovat číslo verze udávajících binární kompatibilitu knihovny.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatické propojení knihovní verze knihovny MFC

Soubory hlaviček MFC automaticky určit správnou verzi knihovny MFC odkaz, na základě hodnot, které jsou definované ve vašem prostředí sestavení. Soubory hlaviček MFC Přidání direktivy kompilátoru propojovací program pro odkaz na konkrétní verzi knihovny MFC.

Například afx –. Soubor hlaviček H dá pokyn linkeru pro odkaz úplné statické, omezené statickou nebo sdílené DLL verze knihovny MFC; ANSI/MBCS nebo Unicode verze; a ladění nebo maloobchodní verze, v závislosti na konfiguraci sestavení:

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

Soubory hlaviček MFC také zahrnovat direktivy pro odkaz v všechny požadované knihoven, včetně knihovny MFC, knihovny Win32, knihoven OLE, knihoven OLE sestaven z ukázky, rozhraní ODBC knihovny a tak dále. 

## <a name="ansi-mbcs-and-unicode"></a>ANSI, kódování Unicode a MBCS

Verze knihovny MFC ANSI/MBCS podporovat obě sady znakovou například ASCII a vícebajtové znakové sady například Shift JIS. Verze knihovny MFC Unicode podporují kódování Unicode v jeho znakové sady UTF-16LE široká charakterová kódované podobě. ANSI/MBCS verze knihovny MFC použijte pro kódování UTF-8 Podpora kódování Unicode.

Pokud chcete nastavit konfiguraci projektu používat jednobajtové, vícebajtové nebo široká charakterová podporu řetězce a znak Unicode v prostředí IDE, použijte **vlastnosti projektu** dialogové okno. V **vlastnosti konfigurace** > **Obecné** nastavte **znaková sada** vlastnost **není nastavena** používat znakovou sadu. Nastavte vlastnost na **použít vícebajtové znakové sady** vícebajtové znakové sady, nebo **používat kódování Unicode znaková sada** používat jako UTF-16 kódování Unicode.

Projekty knihovny MFC použít symbol preprocesoru  **\_UNICODE** udávajících Podpora kódování Unicode široká charakterová UTF-16, a  **\_MBCS** udávajících Podpora znakové sady MBCS. Tyto možnosti se vzájemně vylučují v projektu.

## <a name="mfc-static-library-naming-conventions"></a>Zásady vytváření názvů statické knihovny MFC

Statické knihovny MFC použijte následující zásady vytváření názvů. Názvy knihoven mají tvar

> *u*AFX*c**d*.LIB

zobrazených kurzívou malá písmena, kde jsou zástupné symboly specifikátory jejichž významy jsou uvedeny v následující tabulce:

|Specifikátor|Hodnoty a významy|
|---------------|-------------------------|
|*u*|ANSI/MBCS (ne) nebo Unicode (U); vynechejte pro verzi bez MFC – ovládací prvky v dialogových oknech|
|*c*|Verzi s MFC – ovládací prvky v dialogových oknech (SH) nebo bez (NMCD)|
|*d*|Ladění a vydání: D = Debug; vynechat – specifikátor pro vydání|

Všechny knihovny uvedené v následující tabulce jsou zahrnuty v adresáři \atlmfc\lib pro podporované sestavení architektury předem.

|Knihovna|Popis|
|-------------|-----------------|
|NAFXCW.LIB|Staticky propojené knihovny MFC, prodejní verze|
|NAFXCWD.LIB|Staticky propojené knihovny MFC, ladicí verze|
|UAFXCW.LIB|Staticky propojené knihovny MFC s podporou Unicode, prodejní verze|
|UAFXCWD.LIB|Staticky propojené knihovny MFC s podporou Unicode ladicí verze|
|AFXNMCD.LIB|Staticky propojené knihovny MFC bez ovládací prvky dialogového okna knihovny MFC, prodejní verze|
|AFXNMCDD.LIB|Staticky propojené knihovny MFC bez ovládací prvky dialogového okna knihovny MFC, ladicí verze|

Ladicí program soubory, které mají stejné základním názvem a příponou PDB jsou také k dispozici pro každou z statických knihoven.

## <a name="mfc-shared-dll-naming-conventions"></a>Zásady vytváření názvů knihoven DLL sdílená knihovna MFC

MFC sdílené knihovny DLL také postupujte podle strukturované zásady vytváření názvů. To usnadňuje vědět, které knihovny DLL nebo knihovna by měl použít pro konkrétní účel.

Knihovny MFC DLL mají *verze* čísla označující binární kompatibilitu. Pomocí knihovny MFC DLL, které mají stejnou verzi jako vaše knihovny a sady nástrojů kompilátoru k zajištění kompatibility v rámci projektu.

|DLL|Popis|
|---------|-----------------|
|MFC*verze*. KNIHOVNY DLL|MFC DLL, ANSI nebo MBCS vydání verze|
|MFC*version*U.DLL|MFC DLL, Unicode prodejní verzi|
|MFC*version*D.DLL|Verze knihovny MFC DLL, ANSI nebo ladění MBCS|
|MFC*version*UD.DLL|MFC DLL, Unicode ladicí verze|
|MFCM*verze*. KNIHOVNY DLL|MFC DLL s ovládacími prvky Windows Forms, ANSI nebo MBCS vydání verze|
|MFCM*verze*U.DLL|MFC DLL s ovládacími prvky Windows Forms, Unicode prodejní verzi|
|MFCM*version*D.DLL|MFC DLL s ovládacími prvky Windows Forms, ANSI nebo ladění MBCS verze|
|MFCM*version*UD.DLL|MFC DLL s ovládacími prvky Windows Forms, Unicode ladicí verze|

Importované knihovny potřebné k vytváření aplikací nebo MFC – rozšiřující knihovny DLL, které používají tyto sdílené knihovny DLL mají stejné základní název jako knihovny DLL ale mít příponu názvu souboru LIB. Při použití sdílené knihovny DLL musí být malé statické knihovny stále propojena s kódu; Tato knihovna je s názvem MFCS*verze*.lib {U} {D}.

Pokud vytváříte dynamicky propojení sdílenou knihovnu DLL verze knihovny MFC, zda je z aplikace nebo knihovnu DLL, musí obsahovat odpovídající MFC*verze*. Knihovny DLL nebo MFC*verze*U.DLL při nasazování produktu.

Seznam Visual C++ knihovny DLL, které můžete distribuovat s vašimi aplikacemi najdete v tématu [distribuovatelného kódu pro Microsoft Visual Studio 2017 a Microsoft Visual Studio 2017 SDK (zahrnuje nástroje a soubory buildovacího serveru)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Další informace o rozhraní MBCS a Unicode podporovaných v prostředí MFC najdete v tématu [Podpora vícebajtových znakovou sadu (MBCS) kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Podpora knihovny DLL

Buď statickou nebo sdílené dynamické knihovny MFC slouží k vytvoření knihovny DLL, které mohou být využívána MFC i mimo MFC spustitelné soubory. Toto nastavení se nazývá "regulární knihovny DLL" nebo "regulární knihovny DLL MFC", abychom je odlišili od MFC – rozšiřující knihovny DLL, které může být pouze používá aplikace MFC a knihovna MFC – knihovny DLL. Knihovny DLL vytvořené pomocí statické knihovny MFC se někdy nazývá USRDLL v starší odkazy, protože projekty knihovny MFC DLL definovat symbol preprocesoru  **\_USRDLL**. Knihovny DLL, používá MFC sdílené knihovny DLL se někdy nazývá AFXDLL v starší odkazy, protože definuje symbol preprocesoru  **\_AFXDLL**.

Při vytváření projektu knihovny DLL pomocí propojení statických knihoven MFC, knihovny DLL se dá nasadit bez sdílené knihovny MFC – knihovny DLL. Když projektu knihovny DLL odkazů do knihoven importovat MFC*verze*. LIB nebo MFC*verze*U.LIB, je nutné nasadit shody MFC sdílené knihovny MFC DLL*verze*. Knihovny DLL nebo MFC*verze*U.DLL společně s knihovnou DLL. Další informace najdete v tématu [knihovny DLL](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)  
