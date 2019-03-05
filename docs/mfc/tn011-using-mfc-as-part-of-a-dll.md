---
title: 'TN011: Použití prostředí MFC jako součásti knihovny DLL'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 63e97c3b9260465259d76cf6996d1d389f65ee41
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326449"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Použití prostředí MFC jako součásti knihovny DLL

Tato poznámka popisuje běžné knihovny MFC DLL, které umožňují použít knihovnu MFC jako součásti Windows dynamická knihovna (DLL). Předpokládá, že máte zkušenosti s Windows knihovny DLL a jak je vytvořit. Informace o MFC – rozšiřující knihovny DLL, pomocí které můžete vytvořit rozšíření pro knihovnu MFC, naleznete v tématu [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Rozhraní knihovny DLL

regulární knihovny DLL MFC předpokládat, rozhraní mezi aplikací a knihovny DLL jsou určené v funkcí jazyka C nebo explicitně exportované třídy. Nelze exportovat rozhraní třídy knihovny MFC.

Pokud chcete použít knihovnu MFC DLL a aplikace, mají možnost buď použití sdílených verzí knihovny MFC nebo staticky se propojit ke kopírování knihoven. Aplikace a knihovny DLL může používají jednu standardní verze knihovny MFC.

regulární knihovny DLL MFC mají několik výhod:

- Aplikace, která používá knihovnu DLL není nutné použít knihovnu MFC a nemusí být aplikace v jazyce Visual C++.

- Pomocí běžných knihovnách MFC DLL, která staticky propojené ke knihovně MFC velikost knihovny DLL závisí jenom na rutin modulu runtime MFC a C, které jsou používány a propojené.

- Pomocí běžných knihovnách MFC DLL, která dynamicky propojené ke knihovně MFC Úspora paměti narozdíl od použití sdílených verzí knihovny MFC můžou být významné. Ale musíte distribuovat sdílené knihovny DLL Mfc\<*verze*> .dll a Msvvcrt\<*verze*> DLL s vaší knihovou DLL.

- Knihovna DLL je nezávisle na tom, jak jsou implementované třídy. Návrh knihovny DLL exportuje pouze do rozhraní API, které chcete. Proto pokud se změní implementaci běžných knihovnách MFC DLL jsou stále platné.

- Pomocí běžných knihovnách MFC DLL, která staticky propojené ke knihovně MFC Pokud knihovna DLL a aplikace použít knihovnu MFC, nejsou žádné problémy s aplikací, která požaduje jinou verzi knihovny MFC DLL nebo naopak. Protože knihovny MFC je staticky propojené s každou knihovnu DLL nebo EXE, není žádný dotaz, jakou verzi máte.

## <a name="api-limitations"></a>Omezení rozhraní API

Některé funkce knihovny MFC se nevztahují na verze knihovny DLL, buď z důvodu technická omezení nebo proto, že tyto služby jsou obvykle poskytovaný aplikací. Aktuální verze knihovny MFC, je pouze funkce, která se nedá použít `CWinApp::SetDialogBkColor`.

## <a name="building-your-dll"></a>Building Your DLL

Při kompilaci běžných knihovnách MFC DLL, která staticky propojené ke knihovně MFC, symboly `_USRDLL` a `_WINDLL` musí být definovaný. Váš kód knihovny DLL musí být zkompilovaná následující přepínače kompilátoru:

- **/ D_WINDLL** označuje, že se kompilace pro knihovny DLL

- **/ D_USRDLL** určuje vytváříte běžné knihovny MFC DLL

Musíte také definovat tyto symboly a použijte tyto přepínače kompilátoru při kompilaci běžných knihovnách MFC DLL, která dynamicky propojené ke knihovně MFC. Kromě toho symbol `_AFXDLL` musí být definován a váš kód knihovny DLL musí být kompilována s:

- **/ D_AFXDLL** Určuje, že vytváříte běžné knihovny MFC DLL dynamicky propojuje ke knihovně MFC

Rozhraní (API) mezi aplikace a knihovny DLL musí být explicitně exportován. Doporučujeme definovat vaše rozhraní být s malou šířkou pásma a používat pouze C rozhraní, pokud je to možné. Přímé rozhraní jazyka C jsou snadněji udržovat než složitější třídy jazyka C++.

Umístěte svoje rozhraní API v samostatné záhlaví, který může obsahovat soubory C a C++. Zobrazit záhlaví ScreenCap.h v ukázce MFC Advanced Concepts [DLLScreenCap](../visual-cpp-samples.md) příklad. Pokud chcete exportovat funkce, zadejte je `EXPORTS` části souboru definice modulu (. DEF) nebo zahrnout `__declspec(dllexport)` na vaše definice funkce. Použití `__declspec(dllimport)` naimportujte tyto funkce klientský spustitelný soubor.

Na začátku exportované funkce v běžných knihovnách MFC DLL, která dynamicky propojené ke knihovně MFC, je nutné přidat makro AFX_MANAGE_STATE. Toto makro nastaví aktuální stav modulu pro knihovnu DLL. Pokud chcete použít toto makro, přidejte následující řádek kódu na začátek funkcí exportovaných z knihovny DLL:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

Knihovna MFC definuje standardním Win32 `DllMain` vstupní bod, který inicializuje vaše [CWinApp](../mfc/reference/cwinapp-class.md) odvozenému objektu jako v typické aplikaci knihovny MFC. Umístěte všechny inicializace knihovnu DLL v [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) metody jako v typické aplikaci knihovny MFC.

Všimněte si, že [CWinApp::Run](../mfc/reference/cwinapp-class.md#run) mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní pumpu zpráv. Pokud vaše knihovna DLL zobrazí nemodální dialogová okna, nebo má vlastní okna hlavního rámce, pumpa zpráv vaší aplikace musí volat rutinu Export knihovny DLL, která volá [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Najdete v ukázce DLLScreenCap pro použití této funkce.

`DllMain` Funkce, která knihovna MFC poskytuje, zavolá [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) metoda, která je odvozena z třídy `CWinApp` před uvolněním knihovny DLL.

## <a name="linking-your-dll"></a>Propojování vaší knihovny DLL

Pomocí běžných knihovnách MFC DLL, která staticky propojené ke knihovně MFC je třeba propojit vaši knihovnu DLL Nafxcwd.lib nebo Nafxcw.lib a s verzí modulů runtime jazyka C s názvem Libcmt.lib. Tyto knihovny jsou předem připravená a mohou být nainstalovány službou je zadáte, když spustíte instalační program Visual C++.

## <a name="sample-code"></a>Vzorový kód

Najdete v ukázce MFC Advanced Concepts programu DLLScreenCap úplnou ukázku. Několik zajímavých věcí, Všimněte si v této ukázce jsou následující:

- Příznaky kompilátoru knihovny DLL a těch, které aplikace se liší.

- Odkaz řádky a. DEF soubory pro knihovnu DLL a pro aplikace se liší.

- Aplikace, která používá knihovnu DLL nemusí být v jazyce C++.

- Rozhraní mezi aplikací a knihovna DLL je rozhraní API, který je použitelný pro C nebo C++ a se exportuje s DLLScreenCap.def.

Následující příklad ukazuje rozhraní API, která je definována v běžné knihovny MFC DLL, která staticky propojuje ke knihovně MFC. V tomto příkladu je ohraničen prohlášení `extern "C" { }` bloku pro uživatele jazyka C++. To má několik výhod. Nejprve je vaše rozhraní API knihovny DLL použitelné než C++ klientskými aplikacemi. Za druhé snižuje režijní náklady na knihovnu DLL protože pozměnění názvu C++ se nepoužije pro exportovaný název. A konečně, usnadňuje chcete explicitně přidat do. DEF souboru (pro export podle pořadových čísel) bez nutnosti starat o pozměnění názvu.

```
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

Struktury využívané prostředím rozhraní API nejsou odvozeny od třídy knihovny MFC a jsou definovaná v záhlaví rozhraní API. Tím se sníží složitost rozhraní mezi knihovny DLL a aplikací a znamená použitelné knihovny DLL pomocí programů jazyka C.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
