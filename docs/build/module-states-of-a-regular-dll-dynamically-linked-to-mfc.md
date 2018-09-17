---
title: Stavy modulů běžné knihovny MFC DLL dynamicky propojené ke knihovně MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d458c445930896fb04cb339c7191f649be542faf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717025"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Stavy modulů běžné knihovny MFC DLL dynamicky propojené do MFC

Schopnost běžné knihovny MFC DLL dynamicky propojené ke knihovně MFC DLL umožňuje některé konfigurace, které jsou velmi složité. Například běžné knihovny MFC DLL a spustitelný soubor, který ji používá dynamické propojení ke knihovně MFC DLL a pro jakékoli MFC – rozšiřující knihovny DLL.

Tato konfigurace představuje problém s ohledem na MFC globálních dat, jako je ukazatel na aktuální `CWinApp` mapování objektů a popisovače.

Před MFC verze 4.0 tato globální data nacházejí v knihovně MFC DLL a sdílí všechny moduly v procesu. Protože každý proces pomocí Win32 DLL získá vlastní kopii dat knihovny DLL, toto schéma poskytuje snadný způsob, jak sledovat data na úrovni jednotlivého procesu. Navíc vzhledem k tomu, že AFXDLL model předpokládá, že by existovat pouze jeden `CWinApp` objektu a pouze jednu sadu zpracování mapy v procesu, tyto položky mohou být sledovány v knihovně MFC DLL.

Ale možnost běžné knihovny MFC DLL dynamicky propojené ke knihovně MFC DLL, je možné mít dvě nebo více `CWinApp` objekty v procesu a také dva nebo více sad mapování. Jak knihovna MFC udržovat přehled o ty, které by měla být použita?

Řešením je poskytnout vlastní kopii těchto informací globální stav každého modulu (aplikace nebo běžné knihovny MFC DLL). Proto volání **AfxGetApp** v běžné knihovny MFC DLL vrací ukazatel na `CWinApp` objektů v knihovně DLL není ten ve spustitelném souboru. -Module této kopie globálních dat knihovny MFC se označuje jako modul stavu a je popsána v [MFC technická Poznámka: 58](../mfc/tn058-mfc-module-state-implementation.md).

Běžné proceduru okna knihovny MFC, automaticky se přepne do stavu správný modul proto není nutné si dělat starosti v libovolné obslužné rutiny zpráv, který je implementován v běžné knihovny MFC DLL. Ale když spustitelný soubor volá do běžné knihovny MFC DLL, je nutné explicitně nastavit aktuální stav modulu na jeden z knihovny DLL. Chcete-li to provést, použijte **AFX_MANAGE_STATE** – makro v každé funkci exportovaná z knihovny DLL. To se provádí tak, že přidáte následující řádek kódu na začátek funkcí exportovaných z knihovny DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Správa dat stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)