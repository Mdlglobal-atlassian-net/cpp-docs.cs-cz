---
title: 'TN011: Použití prostředí MFC jako součásti knihovny DLL'
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 0f4d4e2ed76a0fa5f8f775345fc672a1df055a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370429"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Použití prostředí MFC jako součásti knihovny DLL

Tato poznámka popisuje běžné knihovny DLL knihovny Knihovny MFC, které umožňují používat knihovnu knihovny Knihovny MFC jako součást knihovny DLL s dynamickými spojnicemi systému Windows. Předpokládá, že jste obeznámeni s knihovníkem DLL systému Windows a jak je vytvořit. Informace o knihovnách DLL rozšíření knihovny MFC, pomocí kterých můžete vytvořit rozšíření knihovny Knihovny MFC, naleznete [v tématu DLL Verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Rozhraní Knihovny DLL

pravidelné knihovny DLL knihovny MFC předpokládají, že rozhraní mezi aplikací a knihovnou DLL jsou určena ve funkcích podobných c nebo explicitně exportovaných třídách. Rozhraní třídy knihovny MFC nelze exportovat.

Pokud knihovna DLL i aplikace chtějí používat knihovnu MFC, obě mají možnost použít sdílenou verzi knihoven knihovny Knihovny MFC nebo staticky propojit kopii knihoven. Aplikace i knihovna DLL mohou používat jednu ze standardních verzí knihovny knihovny MFC.

běžné knihovny DLL knihovny MFC mají několik výhod:

- Aplikace, která používá knihovnu DLL, nemusí používat knihovnu MFC a nemusí být aplikací visual c++.

- U běžných knihoven DLL knihovny MFC, které staticky odkazují na knihovnu MFC, závisí velikost knihovny DLL pouze na rutinách za běhu knihovny MFC a C, které jsou používány a propojeny.

- U běžných knihoven DLL knihovny MFC, které dynamicky odkazují na knihovnu MFC, může být významné úspory paměti při použití sdílené verze knihovny MFC. Je však nutné distribuovat sdílené knihovny\<DLL,*verzi* knihovny MFC\<>.dll a*msvvcrt verze*>.dll, s knihovnou DLL.

- Návrh dll je nezávislý na tom, jak jsou implementovány třídy. Návrh dll exportuje pouze do rozhraní API, které chcete. V důsledku toho pokud se změní implementace, jsou stále platné běžné knihovny DLL knihovny MFC.

- U běžných knihoven DLL knihovny MFC, které staticky odkazují na knihovnu MFC, pokud knihovna MLL i aplikace používají knihovnu MFC, neexistují žádné problémy s aplikací, která chce jinou verzi knihovny MFC než knihovnu DLL nebo naopak. Vzhledem k tomu, že knihovna knihovny Knihovny MFC je staticky propojena do každé knihovny DLL nebo EXE, není pochyb o tom, kterou verzi máte.

## <a name="api-limitations"></a>Omezení rozhraní API

Některé funkce knihovny MFC se nevztahuje na verzi knihovny DLL, z důvodu technických omezení nebo proto, že tyto služby jsou obvykle poskytovány aplikací. S aktuální verzí knihovny MFC je `CWinApp::SetDialogBkColor`jedinou funkcí, která není použitelná .

## <a name="building-your-dll"></a>Vytváření dll

Při kompilaci běžných knihovny DLL knihovny MFC, `_USRDLL` `_WINDLL` které staticky odkazují na knihovnu MFC, musí být definovány symboly a musí být definovány. Kód DLL musí být také zkompilován s následujícími přepínači kompilátoru:

- **/D_WINDLL** znamená kompilace je pro DLL

- **/D_USRDLL** určuje, že vytváříte pravidelnou knihovnu DLL knihovny MFC.

Musíte také definovat tyto symboly a používat tyto přepínače kompilátoru při kompilaci běžných knihovny DLL knihovny MFC, které dynamicky propojují knihovnu MFC. Kromě toho musí `_AFXDLL` být definován symbol a kód Knihovny DLL musí být kompilován pomocí:

- **/D_AFXDLL** určuje, že vytváříte pravidelnou knihovnu DLL knihovny MFC, která dynamicky odkazuje na knihovnu MFC.

Rozhraní (API) mezi aplikací a knihovnou DLL musí být explicitně exportována. Doporučujeme definovat rozhraní s nízkou šířkou pásma a používat pouze rozhraní C, pokud je to možné. Rozhraní Direct C jsou snadněji udržovatelné než složitější třídy Jazyka C++.

Umístěte vaše API do samostatné hlavičky, která může být zahrnuta do souborů C i C++. Viz záhlaví ScreenCap.h v mfc rozšířené koncepty ukázky [DLLScreenCap](../overview/visual-cpp-samples.md) pro příklad. Chcete-li své funkce exportovat, zadejte je do `EXPORTS` části definičního souboru modulu (. DEF) nebo `__declspec(dllexport)` zahrnout do definice funkcí. Slouží `__declspec(dllimport)` k importu těchto funkcí do spustitelného souboru klienta.

Makro AFX_MANAGE_STATE je nutné přidat na začátek všech exportovaných funkcí v běžných knihovnách DLL knihovny MFC, které dynamicky propojují knihovnu MFC. Toto makro nastaví aktuální stav modulu na stav pro dll. Chcete-li použít toto makro, přidejte na začátek funkcí exportovaných z dll následující řádek kódu:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

Knihovna knihovny MFC definuje `DllMain` standardní vstupní bod Win32, který inicializuje odvozený objekt [CWinApp](../mfc/reference/cwinapp-class.md) jako v typické aplikaci knihovny MFC. Umístěte všechny inicializace specifické pro knihovnu DLL v [initinstance](../mfc/reference/cwinapp-class.md#initinstance) metoda jako v typické aplikace knihovny MFC.

Všimněte si, že [Mechanismus CWinApp::Run](../mfc/reference/cwinapp-class.md#run) se nevztahuje na dll, protože aplikace vlastní hlavní zprávy čerpadlo. Pokud vaše dll zobrazí moderování nebo má vlastní okno hlavního rámce, hlavní zprávy čerpadla aplikace musí volat DLL exportované rutiny, která volá [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Viz ukázka DLLScreenCap pro použití této funkce.

Funkce, kterou knihovna `DllMain` MFC poskytuje, bude volat metodu [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) vaší třídy, která je odvozena před `CWinApp` uvolněním knihovny DLL.

## <a name="linking-your-dll"></a>Propojení dll

U běžných knihoven DLL knihovny MFC, které staticky odkazují na knihovnu MFC, je nutné propojit knihovnu DLL s knihovnou Nafxcwd.lib nebo Nafxcw.lib a s verzí runčase C s názvem Libcmt.lib. Tyto knihovny jsou předem sestavené a mohou být nainstalovány jejich zadáním při spuštění nastavení visual c++.

## <a name="sample-code"></a>Příklad kódu

Kompletní ukázku najdete v ukázkovém programu Knihovny MFC Advanced Concepts DLLScreenCap. Několik zajímavých věcí, které je třeba poznamenat v této ukázce, jsou následující:

- Příznaky kompilátoru dll a ty aplikace se liší.

- Řádky propojení a . DEF soubory pro DLL a ty pro aplikaci se liší.

- Aplikace, která používá dll nemusí být v jazyce C++.

- Rozhraní mezi aplikací a knihovnou DLL je rozhraní API, které je použitelné pomocí jazyka C nebo C++ a je exportováno pomocí souboru DLLScreenCap.def.

Následující příklad ilustruje rozhraní API, které je definováno v běžné knihovně DLL knihovny MFC, která staticky odkazuje na knihovnu MFC. V tomto příkladu je deklarace `extern "C" { }` uzavřena v bloku pro uživatele jazyka C++. To má několik výhod. Nejprve umožňuje vaše DLL API použitelné klientskými aplikacemi bez c++. Za druhé snižuje režii dll, protože c++ název mangling nebude použita na exportovaný název. Nakonec usnadňuje explicitní přidání do . DEF (pro export podle řadového zařízení), aniž byste se museli starat o mangling.

```cpp
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

Struktury používané rozhraním API nejsou odvozeny z tříd knihovny MFC a jsou definovány v hlavičce rozhraní API. To snižuje složitost rozhraní mezi knihovnou DLL a aplikací a umožňuje, aby knihovna DLL byla použitelná programy C.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
