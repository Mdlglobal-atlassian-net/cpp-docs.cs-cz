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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314777"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Běžné knihovny MFC DLL staticky propojené do MFC

Běžná knihovna MFC DLL staticky propojená s knihovnou MFC je knihovna DLL, která interně používá knihovnu MFC a exportované funkce v knihovně DLL mohou být volány spustitelnými soubory MFC nebo non-MFC. Jak popisuje název, tento druh knihovny DLL je sestaven pomocí verze knihovny MFC statického propojení. Funkce jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardního rozhraní jazyka C. Příklad, jak napsat, sestavit a použít regulární knihovnu MFC DLL, naleznete v ukázce [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Všimněte si, že pojem USRDLL již není v dokumentaci Visual C++ používán. Pravidelná knihovna MFC DLL, která je staticky propojena s knihovnou MFC, má stejné charakteristiky jako předchozí USRDLL.

Pravidelná knihovna MFC DLL, staticky propojená s knihovnou MFC, má následující funkce:

- Spustitelný soubor klienta lze zapsat v jakémkoli jazyce, který podporuje použití knihoven DLL (C, C++, Pascal, Visual Basic a tak dále); nemusí to být aplikace MFC.

- Knihovna DLL může odkazovat na stejné knihovny statických odkazů knihovny MFC používané aplikacemi. Pro knihovny DLL už neexistuje samostatná verze statických knihoven odkazů.

- Před verzí 4,0 knihovny MFC poskytoval USRDLL stejný typ funkčnosti jako běžné knihovny MFC DLL staticky propojené s knihovnou MFC. Od Visual C++ verze 4,0 je pojem USRDLL zastaralý.

Pravidelná knihovna MFC DLL, staticky propojená s knihovnou MFC, má následující požadavky:

- Tento typ knihovny DLL musí vytvořit instanci třídy odvozené z `CWinApp`.

- Tento typ knihovny DLL používá modul `DllMain` , který poskytuje knihovna MFC. Všechny inicializační kódy specifické pro DLL umístěte do `InitInstance` členské funkce a ukončovací kód v `ExitInstance` normální aplikaci MFC.

- I když je pojem USRDLL zastaralý, je stále nutné definovat "**_USRDLL**" na příkazovém řádku kompilátoru. Tato definice určuje, které deklarace jsou získány ze souborů hlaviček knihovny MFC.

běžné knihovny MFC DLL musí mít `CWinApp`třídu odvozenou od třídy a jeden objekt třídy aplikace, stejně jako aplikace MFC. Nicméně `CWinApp` objekt knihovny DLL nemá hlavní čerpadlo zpráv, stejně jako `CWinApp` objekt aplikace.

Všimněte si, `CWinApp::Run` že mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní pumpu zpráv. Pokud knihovna DLL otevře nemodální dialogová okna nebo má hlavní okno rámce vlastní, musí hlavní pumpa zpráv aplikace volat rutinu exportovanou knihovnou DLL, která zase volá `CWinApp::PreTranslateMessage` členskou funkci objektu aplikace knihovny DLL.

Příklad této funkce naleznete v ukázce DLLScreenCap.

Symboly jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardního rozhraní jazyka C. Deklarace funkce exportované z běžné knihovny MFC DLL by vypadala přibližně takto:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Všechna přidělení paměti v rámci běžné knihovny MFC DLL by měla zůstat v rámci knihovny DLL; Knihovna DLL by neměla předávat ani přijímat volání z následujících spustitelných souborů:

- Ukazatelé na objekty MFC

- Ukazatelé na paměť přidělenou knihovnou MFC

Pokud potřebujete provést některý z výše uvedených kroků nebo potřebujete předat objekty odvozené od knihovny MFC mezi volajícím spustitelným souborem a knihovnou DLL, je nutné vytvořit rozšiřující knihovnu DLL knihovny MFC.

Je bezpečné předat ukazatelům do paměti, které byly přiděleny knihovnami run-time jazyka C mezi aplikací a knihovnou DLL pouze v případě, že vytvoříte kopii dat. Nesmíte odstranit ani změnit velikost těchto ukazatelů ani je použít bez toho, aby bylo možné vytvořit kopii paměti.

Knihovna DLL, která je staticky propojena s knihovnou MFC, nemůže také dynamicky propojit sdílené knihovny MFC DLL. Knihovna DLL, která je staticky propojena s knihovnou MFC, je dynamicky svázána s aplikací stejně jako jakákoli jiná knihovna DLL. aplikace na ni odkazují stejně jako všechny jiné knihovny DLL.

Standardní knihovny statických odkazů knihovny MFC jsou pojmenovány podle konvence popsaných v tématu zásady [vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Avšak s knihovnou MFC verze 3,0 a novější již není nutné ručně zadávat do linkeru verzi knihovny MFC, kterou chcete propojit. Místo toho soubory hlaviček knihovny MFC automaticky určí správnou verzi knihovny MFC, která bude propojena v závislosti na definici preprocesoru, jako je například ** \_ladění** nebo **_UNICODE**. Soubory hlaviček knihovny MFC přidávají/DEFAULTLIB direktivy, které řídí linker k propojení v konkrétní verzi knihovny MFC.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializovat běžné knihovny MFC DLL](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Použití knihovny MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Vytvoření knihovny MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [Běžné knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC – rozšiřující knihovny DLL](extension-dlls-overview.md)

## <a name="see-also"></a>Viz také

[Druhy knihoven DLL](kinds-of-dlls.md)
