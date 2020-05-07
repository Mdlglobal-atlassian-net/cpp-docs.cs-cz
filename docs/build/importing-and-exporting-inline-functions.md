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
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328516"
---
# <a name="importing-and-exporting-inline-functions"></a>Import a export vložených funkcí

Importované funkce lze definovat jako vložené. Efekt je zhruba stejný jako při definování standardní vložené funkce. volání funkce jsou rozšířena do vloženého kódu, podobně jako makro. To je v podstatě užitečné jako podpora tříd C++ v knihovně DLL, která by mohla začlenit některé jejich členské funkce na efektivitu.

Jednou z funkcí importované vložené funkce je to, že můžete získat svou adresu v jazyce C++. Kompilátor vrátí adresu kopie vložené funkce, která je umístěna v knihovně DLL. Další funkcí importovaných vložených funkcí je, že můžete inicializovat statická místní data importované funkce na rozdíl od globálních importovaných dat.

> [!CAUTION]
> Při poskytování importovaných vložených funkcí byste měli věnovat pozornost, protože můžou vytvořit možnost konfliktu verzí. Vložená funkce se rozšíří do kódu aplikace; Proto pokud později znovu zapíšete funkci, nebude aktualizována, pokud aplikace samotná nebude znovu zkompilována. (Obvykle se funkce knihoven DLL dají aktualizovat bez nutnosti znovu sestavovat aplikace, které je používají.)

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL](exporting-from-a-dll.md)

- [Exportujte z knihovny DLL pomocí. Soubory DEF](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Viz také

[Import a export](importing-and-exporting.md)
