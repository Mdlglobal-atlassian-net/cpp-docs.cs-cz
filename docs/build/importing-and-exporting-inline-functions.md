---
title: Import a export vložených funkcí
ms.date: 11/04/2016
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
ms.openlocfilehash: ed523d84228124d4a8d99e443c0c744f362f1c56
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822038"
---
# <a name="importing-and-exporting-inline-functions"></a>Import a export vložených funkcí

Jako vloženou lze definovat importované funkce. Efekt je přibližně stejná jako definice vloženě standardní funkci; volání funkce jsou rozbalena do vloženého kódu, podobně jako makra. To je užitečné především jako způsob podpory C++ tříd v knihovně DLL může přímo tady některé z jejich členské funkce efektivitu.

Jednu funkci vložené importované funkce je, že může trvat adresy v jazyce C++. Kompilátor vrátí adresu kopii vložená funkce, které se nacházejí v knihovně DLL. Další funkcí importovaných vložených funkcí je, že inicializace statická místní data importované funkce, na rozdíl od globální importovaná data.

> [!CAUTION]
>  Jste měli buďte opatrní při poskytování importu vložené funkce, protože možnost konflikty verzí mohou vytvářet. Vložená funkce se rozbalí do kódu aplikace; Proto pokud později přepsat funkci, se neaktualizuje Pokud samotná aplikace přepsán. (Za normálních okolností funkcí knihovny DLL je možné aktualizovat bez nutnosti opětovného sestavení aplikace, které je používají.)

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL](exporting-from-a-dll.md)

- [Export z knihovny DLL pomocí. DEF soubory](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určit, kterou exportovací metodu použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Viz také:

[Import a export](importing-and-exporting.md)
