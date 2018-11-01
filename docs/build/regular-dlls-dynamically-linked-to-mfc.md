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
ms.openlocfilehash: 550391d51560ff0beca8252ffb6193dd1e4d89b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632385"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Běžné knihovny MFC DLL staticky propojené do MFC

Knihovnu DLL, která používá knihovnu MFC interně je běžný, které knihovny MFC DLL staticky propojené do MFC a spustitelnými soubory knihovny MFC nebo knihovny non-MFC lze volat exportované funkce v knihovně DLL. Podle popisu v názvu, je tento druh knihovny DLL vytvořené pomocí knihovny DLL verze knihovny MFC (označované také jako sdílených verzí knihovny MFC). Funkce jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardních rozhraní C.

Je nutné přidat `AFX_MANAGE_STATE` – makro na začátku exportované funkce v běžných knihovnách MFC DLL, která dynamicky propojené ke knihovně MFC k nastavení aktuální stav modulu pro knihovnu DLL. To se provádí tak, že přidáte následující řádek kódu na začátek funkcí exportovaných z knihovny DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Běžné knihovny MFC DLL staticky propojené do MFC má následující funkce:

- Toto je nový typ knihovny DLL zavedených v aplikaci Visual C++ 4.0.

- Klientský spustitelný soubor lze zapsat v libovolném jazyce, který podporuje použití knihoven DLL (C, C++, Pascal, Visual Basic a tak dále); nemusí být aplikace knihovny MFC.

- Na rozdíl od staticky propojených běžné knihovny MFC DLL tento typ knihovny DLL dynamicky propojené ke knihovně MFC DLL (označované také jako sdílená knihovna MFC DLL).

- Importovat knihovny MFC propojené s DLL tento typ je stejný jako ten použitý pro rozšiřující knihovny DLL MFC nebo aplikace používající knihovnu MFC DLL: lib MFCxx (D).

Běžné knihovny MFC DLL dynamicky propojené ke knihovně MFC mají následující požadavky:

- Tyto knihovny DLL se kompilují pomocí **_AFXDLL** definované, stejně jako spustitelný soubor, který je dynamicky propojené ke knihovně MFC DLL. Ale **_USRDLL** je také definováno, stejně jako běžné knihovny MFC DLL staticky propojené do MFC.

- Musíte vytvořit instanci tohoto typu knihovny DLL `CWinApp`-odvozené třídy.

- Tento typ používá knihovnu DLL `DllMain` poskytované knihovny MFC. Umístit všechny kód inicializace knihovnu DLL `InitInstance` členské funkce a ukončovacího kódu v `ExitInstance` stejně jako v běžné aplikace knihovny MFC.

Vzhledem k tomu používá tento druh knihovny DLL verze knihovny MFC, musíte explicitně nastavit aktuální stav modulu na jeden z knihovny DLL. Chcete-li to provést, použijte [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) – makro na začátku každé funkce exportovaná z knihovny DLL.

regulární knihovny DLL MFC musí mít `CWinApp`-odvozené třídy a jeden objekt třídy aplikace, stejně jako aplikace knihovny MFC. Ale `CWinApp` objekt knihovny DLL nemá hlavní zprávy odeslané, stejně jako `CWinApp` objektu aplikace.

Všimněte si, že `CWinApp::Run` mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní pumpu zpráv. Pokud vaše knihovna DLL přináší nemodální dialogová okna, nebo má vlastní okna hlavního rámce, pumpa zpráv vaší aplikace musí volat rutinu Export knihovny DLL, která volá `CWinApp::PreTranslateMessage`.

Umístěte všechny inicializace knihovnu DLL v `CWinApp::InitInstance` členské funkce stejně jako v běžné aplikace knihovny MFC. `CWinApp::ExitInstance` Členskou funkci vaše `CWinApp` odvozené třídy je volána z knihovny MFC k dispozici `DllMain` funkce před uvolněním knihovny DLL.

Musíte distribuovat sdílené knihovny DLL MFCx0.dll a Msvcr*0.dll (nebo podobné soubory) s vaší aplikací.

Knihovnu DLL, která je dynamicky propojené ke knihovně MFC nemůže být staticky propojena s knihovnou MFC. Odkaz aplikace na běžných knihovnách MFC DLL staticky propojené do MFC je stejně jako ostatní knihovny DLL.

Symboly jsou obvykle exportovány z běžné knihovny MFC DLL pomocí standardních rozhraní C. Deklarace funkce exportované z běžné knihovny MFC DLL vypadá přibližně takto:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Všechna přidělení paměti v rámci běžné knihovny MFC DLL by mělo zůstat v rámci knihovny DLL; Knihovna DLL by neměla předat do nebo přijímat volání spustitelnému souboru kterýkoli z následujících:

- ukazatelé na objekty MFC

- ukazatele na paměť přidělenou v prostředí MFC

Pokud je potřeba provádět žádnou z výše uvedených nebo pokud je potřeba předávat voláním spustitelného souboru a knihovny DLL MFC odvozené objekty, musíte sestavit rozšiřující knihovny DLL MFC.

Je bezpečné předat ukazatele na paměti, které byly přiděleny podle běhových knihoven C mezi aplikace a knihovny DLL pouze v případě, že můžete vytvořit kopii data. Nesmí odstranění nebo změna velikosti tyto ukazatele nebo použít bez vytvoření kopie paměti.

Při sestavování obvyklé knihovny DLL MFC, která dynamicky propojuje ke knihovně MFC, je třeba použít makra [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) pro přepnutí stavu modulu MFC správně. To se provádí tak, že přidáte následující řádek kódu na začátek funkcí exportovaných z knihovny DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

**AFX_MANAGE_STATE** – makro není vhodné používat v běžných knihovnách MFC DLL, která staticky se propojit s knihovnou MFC nebo v MFC – rozšiřující knihovny DLL. Další informace najdete v tématu [Správa stavu Data modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Příklad toho, jak zapisovat, vytvářet a využívat běžné knihovny MFC DLL, najdete v ukázce [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Další informace o běžných knihovnách MFC DLL, která dynamicky propojené ke knihovně MFC naleznete v části s názvem "Převod DLLScreenCap k dynamické propojení s knihovnou MFC DLL" v abstraktní pro vzorku.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializovat obvyklé knihovny DLL MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Stavy modulů běžné knihovny MFC DLL dynamicky propojené do MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Správa dat stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Viz také

[Typy knihoven DLL](../build/kinds-of-dlls.md)