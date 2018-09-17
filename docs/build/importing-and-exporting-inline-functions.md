---
title: Import a export vložených funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431b7c3becffb4e5b2543984fd66cae0a1507738
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726554"
---
# <a name="importing-and-exporting-inline-functions"></a>Import a export vložených funkcí

Jako vloženou lze definovat importované funkce. Efekt je přibližně stejná jako definice vloženě standardní funkci; volání funkce jsou rozbalena do vloženého kódu, podobně jako makra. To je užitečné především jako způsob podpory C++ tříd v knihovně DLL může přímo tady některé z jejich členské funkce efektivitu.

Jednu funkci vložené importované funkce je, že může trvat adresy v jazyce C++. Kompilátor vrátí adresu kopii vložená funkce, které se nacházejí v knihovně DLL. Další funkcí importovaných vložených funkcí je, že inicializace statická místní data importované funkce, na rozdíl od globální importovaná data.

> [!CAUTION]
>  Jste měli buďte opatrní při poskytování importu vložené funkce, protože možnost konflikty verzí mohou vytvářet. Vložená funkce se rozbalí do kódu aplikace; Proto pokud později přepsat funkci, se neaktualizuje Pokud samotná aplikace přepsán. (Za normálních okolností funkcí knihovny DLL je možné aktualizovat bez nutnosti opětovného sestavení aplikace, které je používají.)

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL](../build/exporting-from-a-dll.md)

- [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Viz také

[Import a export](../build/importing-and-exporting.md)