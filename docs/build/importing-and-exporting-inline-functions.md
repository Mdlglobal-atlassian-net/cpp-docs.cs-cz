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

Importované funkce lze definovat jako vložky. Efekt je zhruba stejný jako definování standardní funkce vřádkové; volání funkce jsou rozbaleny do vřádkového kódu, podobně jako makro. To je hlavně užitečné jako způsob podpory tříd jazyka C++ v dll, které mohou vřadit některé z jejich členských funkcí pro efektivitu.

Jednou z funkcí importované vřádkové funkce je, že můžete vzít jeho adresu v jazyce C++. Kompilátor vrátí adresu kopie vřádkové funkce s bydlištěm v dll. Další funkcí importovaných vložkových funkcí je, že na rozdíl od globálních importovaných dat můžete inicializovat statická místní data importované funkce.

> [!CAUTION]
> Při poskytování importovaných vložkových funkcí byste měli postupovat opatrně, protože mohou vytvářet možnost konfliktů verzí. Funkce inline se rozbalí do kódu aplikace; Proto pokud později přepsat funkci, není získat aktualizovány, pokud samotná aplikace je znovu zkompilován. (Normálně lze funkce dll aktualizovat bez opětovného sestavení aplikací, které je používají.)

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z dll.](exporting-from-a-dll.md)

- [Exportujte z dll pomocí . DEF soubory](exporting-from-a-dll-using-def-files.md)

- [Export z dll pomocí __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Viz také

[Import a export](importing-and-exporting.md)
