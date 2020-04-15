---
title: CString – předávání argumentů
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317937"
---
# <a name="cstring-argument-passing"></a>CString – předávání argumentů

Tento článek vysvětluje, jak předat [CString](../atl-mfc-shared/reference/cstringt-class.md) objekty `CString` funkce a jak vrátit objekty z funkcí.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>CString Argument-Passing konvence

Při definování rozhraní třídy je nutné určit konvence předávání argumentů pro členské funkce. Existují některá standardní pravidla pro `CString` předávání a vracení objektů. Pokud budete postupovat podle pravidel popsaných v [řetězce jako vstupy funkce](#_core_strings_as_function_inputs) a řetězce jako [výstupy funkce](#_core_strings_as_function_outputs), budete mít efektivní, správný kód.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>Řetězce jako vstupy funkcí

Nejúčinnější a nejbezpečnější způsob, `CString` jak používat objekt v `CString` volané funkce je předat objekt do funkce. Navzdory názvu `CString` objekt neukládá řetězec interně jako řetězec stylu C, který má zakončení null. Místo toho `CString` objekt pečlivě sleduje počet znaků, které má. Po `CString` poskytnutí LPCTSTR ukazatel na řetězec ukončennul nula je malé množství práce, které se může stát významné, pokud váš kód má to udělat neustále. Výsledek je dočasný, protože `CString` jakákoli změna obsahu zruší platnost starých kopií ukazatele LPCTSTR.

V některých případech má smysl poskytovat řetězec ve stylu C. Například může nastat situace, kdy je volaná funkce zapsána v C a nepodporuje objekty. V tomto případě dosáhejte `CString` parametr lPCTSTR a funkce získá řetězec ukončený ve stylu C. Můžete také přejít opačným `CString` směrem a `CString` vytvořit objekt pomocí konstruktoru, který přijímá parametr řetězce ve stylu C.

Pokud má být obsah řetězce změněn funkcí, deklarujte `CString` parametr`CString&`jako nekonstantní odkaz ( ).

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>Řetězce jako výstupy funkcí

Obvykle můžete vrátit `CString` objekty `CString` z funkcí, protože objekty sledovat hodnotu sémantiku jako primitivní typy. Chcete-li vrátit řetězec jen pro `CString` čtení, použijte konstantní odkaz (`const CString&`). Následující příklad ilustruje použití `CString` parametrů a návratových typů:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Viz také

[Řetězce (KNIHOVNA ATL/Knihovna Knihovny AFC)](../atl-mfc-shared/strings-atl-mfc.md)
