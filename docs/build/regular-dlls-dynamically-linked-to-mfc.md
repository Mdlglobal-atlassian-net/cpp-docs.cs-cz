---
title: Běžné knihovny MFC DLL staticky propojené do MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314998"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Běžné knihovny MFC DLL staticky propojené do MFC

Běžná knihovna MFC DLL dynamicky propojená s knihovnou MFC je knihovna DLL, která interně používá knihovnu MFC a exportované funkce v knihovně DLL mohou být volány spustitelnými soubory MFC nebo non-MFC. Jak název popisuje, tento druh knihovny DLL je sestaven pomocí verze knihovny MFC dynamického propojení (označované také jako sdílená verze knihovny MFC). Funkce jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardního rozhraní jazyka C.

Je nutné přidat `AFX_MANAGE_STATE` makro na začátek všech exportovaných funkcí v běžných knihovnách MFC DLL, které dynamicky odkazují na knihovnu MFC, a nastavit tak aktuální stav modulu na jednu pro knihovnu DLL. To se provádí přidáním následujícího řádku kódu na začátek funkcí exportovaných z knihovny DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Běžná knihovna MFC DLL, dynamicky propojená s knihovnou MFC, má následující funkce:

- Toto je nový typ knihovny DLL, kterou zavádí Visual C++ 4,0.

- Spustitelný soubor klienta lze zapsat v jakémkoli jazyce, který podporuje použití knihoven DLL (C, C++, Pascal, Visual Basic a tak dále); nemusí to být aplikace MFC.

- Na rozdíl od staticky propojené běžné knihovny MFC DLL je tento typ knihovny DLL dynamicky propojen s knihovnou MFC DLL (označuje se také jako sdílená knihovna MFC DLL).

- Knihovna importu knihovny MFC propojená s tímto typem knihovny DLL je stejná jako ta, která se používá pro knihovny DLL rozšíření MFC nebo pro aplikace pomocí knihovny MFC DLL: MFCxx (D). lib.

Běžná knihovna MFC DLL, dynamicky propojená s knihovnou MFC, má následující požadavky:

- Tyto knihovny DLL jsou kompilovány s definovaným **_AFXDLL** , stejně jako spustitelný soubor, který je dynamicky propojen s knihovnou MFC DLL. Ale **_USRDLL** je také definováno stejně jako běžná knihovna MFC DLL, která je staticky propojena s knihovnou MFC.

- Tento typ knihovny DLL musí vytvořit instanci `CWinApp`odvozené třídy.

- Tento typ knihovny DLL používá modul `DllMain` , který poskytuje knihovna MFC. Všechny inicializační kódy specifické pro DLL umístěte do `InitInstance` členské funkce a ukončovací kód v `ExitInstance` normální aplikaci MFC.

Vzhledem k tomu, že tento druh knihovny DLL používá dynamickou knihovnu knihovny MFC, je nutné explicitně nastavit aktuální stav modulu na jednu pro knihovnu DLL. Chcete-li to provést, použijte makro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) na začátku každé funkce exportované z knihovny DLL.

běžné knihovny MFC DLL musí mít `CWinApp`třídu odvozenou od třídy a jeden objekt třídy aplikace, stejně jako aplikace MFC. Nicméně `CWinApp` objekt knihovny DLL nemá hlavní čerpadlo zpráv, stejně jako `CWinApp` objekt aplikace.

Všimněte si, `CWinApp::Run` že mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní pumpu zpráv. Pokud vaše knihovna DLL obsahuje nemodální dialogová okna nebo má hlavní okno rámce vlastní, musí hlavní pumpa zpráv vaší aplikace volat rutinu exportovanou z knihovny DLL, `CWinApp::PreTranslateMessage`která volá.

Všechny inicializace specifické pro knihovnu DLL umístěte do `CWinApp::InitInstance` členské funkce jako v normální aplikaci knihovny MFC. `CWinApp::ExitInstance` Členská funkce `CWinApp` odvozené třídy je volána z poskytnuté `DllMain` funkce knihovny MFC před uvolněním knihovny DLL.

Sdílené knihovny DLL MFCx0. dll a MSVCR * 0. dll (nebo podobné soubory) musíte distribuovat do své aplikace.

Knihovna DLL, která je dynamicky propojena s knihovnou MFC, nemůže také staticky propojit s knihovnou MFC. Aplikace odkazují na běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC stejně jako jakékoli jiné knihovny DLL.

Symboly jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardního rozhraní jazyka C. Deklarace funkce exportované z běžné knihovny MFC DLL vypadá nějak takto:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Všechna přidělení paměti v rámci běžné knihovny MFC DLL by měla zůstat v rámci knihovny DLL; Knihovna DLL by neměla předávat ani přijímat volání z následujících spustitelných souborů:

- ukazatelé na objekty MFC

- ukazatelé na paměť přidělenou knihovnou MFC

Pokud potřebujete provést některou z výše uvedených nebo pokud potřebujete předat objekty odvozené od knihovny MFC mezi volajícím spustitelným souborem a knihovnou DLL, je nutné sestavit rozšiřující knihovnu DLL knihovny MFC.

Je bezpečné předat ukazatelům do paměti, které byly přiděleny knihovnami run-time jazyka C mezi aplikací a knihovnou DLL pouze v případě, že vytvoříte kopii dat. Nesmíte odstranit ani změnit velikost těchto ukazatelů ani je použít bez toho, aby bylo možné vytvořit kopii paměti.

Při sestavování běžné knihovny MFC DLL, která dynamicky propojuje ke knihovně MFC, je nutné použít makro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) pro správné přepnutí stavu modulu MFC. To se provádí přidáním následujícího řádku kódu na začátek funkcí exportovaných z knihovny DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Makro **AFX_MANAGE_STATE** by nemělo být použito v běžných knihovnách MFC DLL, které staticky odkazují na knihovnu MFC nebo knihovny DLL rozšíření MFC. Další informace naleznete v tématu [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Příklad, jak napsat, sestavit a použít regulární knihovnu MFC DLL, naleznete v ukázce [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Další informace o běžných knihovnách MFC DLL, které dynamicky odkazují na knihovnu MFC, naleznete v části s názvem "převod DLLScreenCap na dynamické propojení s knihovnou MFC DLL" v abstraktu pro ukázku.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializovat běžné knihovny MFC DLL](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Stavy modulů běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Použití knihovny MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Viz také

[Druhy knihoven DLL](kinds-of-dlls.md)
