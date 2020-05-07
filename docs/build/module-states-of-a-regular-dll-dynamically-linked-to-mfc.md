---
title: Stavy modulů běžné knihovny MFC DLL dynamicky propojené do MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220580"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Stavy modulů běžné knihovny MFC DLL dynamicky propojené do MFC

Možnost dynamického propojení běžné knihovny MFC DLL k knihovně MFC DLL umožňuje některé konfigurace velmi složité. Například běžná knihovna MFC DLL a spustitelný soubor, který je používá, mohou být dynamicky propojeny s knihovnou MFC DLL a všemi rozšiřujícími knihovnami DLL knihovny MFC.

Tato konfigurace představuje problém s ohledem na globální data knihovny MFC, jako je například ukazatel na aktuální `CWinApp` objekt a mapování popisovačů.

Před knihovnou MFC verze 4,0 tato globální data jsou uložena v samotné knihovně MFC DLL a sdílena všemi moduly v procesu. Vzhledem k tomu, že každý proces využívající Win32 DLL získá svoji vlastní kopii dat knihovny DLL, toto schéma poskytuje snadný způsob, jak sledovat data jednotlivých procesů. Vzhledem k tomu, že model AFXDLL – předpokládá, že v procesu by byl `CWinApp` pouze jeden objekt a pouze jedna sada map popisovačů, mohou být tyto položky sledovány v samotné knihovně MFC DLL.

Ale s možností dynamického propojení běžné knihovny MFC DLL k knihovně MFC DLL je nyní možné mít dva nebo více `CWinApp` objektů v procesu – a také dvě nebo více sad map popisovačů. Jak aplikace MFC udržuje přehled o tom, která z nich by měla používat?

Řešením je poskytnout každému modulu (aplikaci nebo běžné knihovně MFC DLL) svou vlastní kopii těchto globálních informací o stavu. Proto volání **AfxGetApp** v běžné knihovně MFC DLL vrátí ukazatel na `CWinApp` objekt v knihovně DLL, nikoli ve spustitelném souboru. Tato kopie globálních dat knihovny MFC pro jednotlivé moduly je označována jako stav modulu a je popsána v [knihovně MFC tech Note 58](../mfc/tn058-mfc-module-state-implementation.md).

Standardní procedura okna knihovny MFC automaticky přepne do správného stavu modulu, takže se o ně nemusíte starat v jakýchkoli obslužných rutinách zpráv implementovaných v běžné knihovně MFC DLL. Ale když spustitelný soubor volá do běžné knihovny MFC DLL, je nutné explicitně nastavit aktuální stav modulu na jednu pro knihovnu DLL. Chcete-li to provést, použijte makro **AFX_MANAGE_STATE** v každé funkci exportované z knihovny DLL. To se provádí přidáním následujícího řádku kódu na začátek funkcí exportovaných z knihovny DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC – rozšiřující knihovny DLL](extension-dlls-overview.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
