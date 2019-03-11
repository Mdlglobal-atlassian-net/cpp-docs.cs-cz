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
ms.openlocfilehash: 1729167786d71c107fe6a4369d5a0c7e7c8594f1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742191"
---
# <a name="cstring-argument-passing"></a>CString – předávání argumentů

Tento článek vysvětluje, jak předat [CString](../atl-mfc-shared/reference/cstringt-class.md) objektů funkce a jak vrátit `CString` objekty z funkce.

##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString – předávání argumentů konvence

Při definování třídy rozhraní, musíte určit konvence předávání argumentů pro členské funkce. Existují některé standardní pravidla pro předávání a vracení `CString` objekty. Pokud budete postupovat podle pravidel popsaných v [řetězců jako vstupy funkce](#_core_strings_as_function_inputs) a [řetězců jako výstup funkce](#_core_strings_as_function_outputs), budete mít efektivní, správný kód.

##  <a name="_core_strings_as_function_inputs"></a> Řetězce jako vstupy – funkce

Nejvíce efektivní a zabezpečený způsob, jak používat `CString` objekt ve volané funkce je k předání `CString` objektu funkce. Bez ohledu na název `CString` objekt neukládá řetězec interně jako řetězec stylu C, který má ukončovací znak null. Místo toho `CString` objekt opatrní sleduje počet znaků, obsahuje. S `CString` malé množství práce, která se může stát důležité, pokud má váš kód provést neustále se LPCTSTR ukazatel na řetězec zakončený hodnotou null. Výsledkem je dočasný, protože jakékoli změny `CString` obsah zruší platnost stará kopie LPCTSTR ukazatele.

To dává smysl v některých případech k poskytování řetězec C-style. Například může být situaci, kdy volaná funkce je napsána v jazyce C a nepodporuje objekty. V takovém případě převedeno `CString` parametr LPCTSTR a funkce se zobrazí řetězec stylu C zakončený hodnotou null. Můžete také přejít opačným směrem a vytvořit `CString` s použitím `CString` konstruktor, který přijímá řetězcový parametr C-style.

Obsah řetězce mají-li změnit tak funkce, deklaraci parametru jako nonconstant `CString` odkaz (`CString&`).

##  <a name="_core_strings_as_function_outputs"></a> Řetězců jako výstup – funkce

Obvykle se můžete vrátit `CString` objekty z funkcí, protože `CString` objekty podle hodnoty sémantiku jako primitivní typy. Chcete-li vrátit řetězec jen pro čtení, použijte konstantu `CString` odkaz (`const CString&`). Následující příklad ukazuje použití `CString` parametry a návratové typy:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Viz také:

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
