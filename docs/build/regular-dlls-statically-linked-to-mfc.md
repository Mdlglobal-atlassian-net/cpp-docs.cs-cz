---
title: Běžné knihovny MFC DLL staticky propojené do MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815798"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Běžné knihovny MFC DLL staticky propojené do MFC

Knihovnu DLL, která používá knihovnu MFC interně je běžný, které knihovny MFC DLL staticky propojené do MFC a spustitelnými soubory knihovny MFC nebo knihovny non-MFC lze volat exportované funkce v knihovně DLL. Podle popisu v názvu, je tento druh knihovny DLL vytvořené pomocí statické propojení knihovní verze knihovny MFC. Funkce jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardních rozhraní C. Příklad toho, jak zapisovat, vytvářet a využívat běžné knihovny MFC DLL, najdete v ukázce [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Všimněte si, že v dokumentaci k Visual C++ se již nepoužívá termín USRDLL. Běžné knihovny MFC DLL staticky propojené do MFC má stejné vlastnosti jako dosavadní USRDLL.

Běžné knihovny DLL MFC staticky propojené do MFC, má následující funkce:

- Klientský spustitelný soubor lze zapsat v libovolném jazyce, který podporuje použití knihoven DLL (C, C++, Pascal, Visual Basic a tak dále); nemusí být aplikace knihovny MFC.

- Knihovny DLL můžete propojit stejným statickém propojení knihoven MFC používané aplikacemi. Je již nebude samostatnou verzi knihovny statických odkazů pro knihovny DLL.

- Dříve než ve verzi 4.0 knihovna MFC poskytuje USRDLL stejného typu funkce jako obvyklé knihovny MFC DLL staticky propojené do MFC. Od verze Visual C++ verze 4.0, termín USRDLL je zastaralý.

Běžné knihovny DLL MFC staticky propojené do MFC, má následující požadavky:

- Tento druh knihovny DLL musíte vytvořit instanci třídy odvozené od `CWinApp`.

- Tento typ používá knihovnu DLL `DllMain` poskytované knihovny MFC. Umístit všechny kód inicializace knihovnu DLL `InitInstance` členské funkce a ukončovacího kódu v `ExitInstance` stejně jako v běžné aplikace knihovny MFC.

- Přestože termín USRDLL je zastaralý, je nutné definovat "**_USRDLL**" na příkazový řádek kompilátoru. Tato definice určuje, které deklarace se použije souborech hlaviček knihovny MFC.

regulární knihovny DLL MFC musí mít `CWinApp`-odvozené třídy a jeden objekt třídy aplikace, stejně jako aplikace knihovny MFC. Ale `CWinApp` objekt knihovny DLL nemá hlavní zprávy odeslané, stejně jako `CWinApp` objektu aplikace.

Všimněte si, že `CWinApp::Run` mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní pumpu zpráv. Pokud knihovna DLL otevře nemodální dialogová okna, nebo má vlastní okna hlavního rámce, pumpa zpráv aplikace musí volat rutinu exportovaných knihovnou DLL, která volá `CWinApp::PreTranslateMessage` členské funkce objektu aplikaci knihovny DLL.

Příklad této funkce najdete v ukázce DLLScreenCap.

Symboly jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardních rozhraní C. Deklarace funkce exportované z běžné knihovny MFC DLL by vypadat přibližně takto:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Všechna přidělení paměti v rámci běžné knihovny MFC DLL by mělo zůstat v rámci knihovny DLL; Knihovna DLL by neměla předat do nebo přijímat volání spustitelnému souboru kterýkoli z následujících:

- ukazatelé na objekty MFC

- ukazatele na paměť přidělenou v prostředí MFC

Pokud je potřeba provádět žádnou z výše uvedených nebo potřebujete předat mezi voláním spustitelného souboru a knihovny DLL MFC odvozené objekty, musíte sestavit rozšiřující knihovny DLL MFC.

Je bezpečné předat ukazatele na paměti, které byly přiděleny podle běhových knihoven C mezi aplikace a knihovny DLL pouze v případě, že můžete vytvořit kopii data. Nesmí odstranění nebo změna velikosti tyto ukazatele nebo použít bez vytvoření kopie paměti.

Knihovnu DLL, která je staticky propojené do MFC nelze propojit také dynamické sdílené knihovny MFC DLL. Knihovnu DLL, která je staticky propojené do MFC je dynamicky vázán k aplikaci stejně jako ostatní knihovny DLL; aplikace je odkaz na něj stejně jako ostatní knihovny DLL.

Standardní statickém propojení knihoven MFC jsou pojmenovány podle konvence je popsáno v [zásady vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). S knihovnou MFC verze 3.0 nebo novější, je však již nebude nutné ručně zadat do linkeru verzi knihovny MFC, kterou chcete propojit. Soubory hlaviček knihovny MFC místo toho automaticky určit, definuje správnou verzi knihovny MFC pro propojení v závislosti na preprocesoru, jako například  **\_ladění** nebo **_UNICODE**. Soubory hlaviček knihovny MFC Přidání direktivy /DEFAULTLIB propojovací program na odkaz v konkrétní verzi knihovny MFC.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializovat obvyklé knihovny DLL MFC](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Vytváření knihovny MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [Běžné knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC – rozšiřující knihovny DLL](extension-dlls-overview.md)

## <a name="see-also"></a>Viz také:

[Typy knihoven DLL](kinds-of-dlls.md)
