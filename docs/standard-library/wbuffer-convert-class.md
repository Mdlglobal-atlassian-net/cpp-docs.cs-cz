---
title: wbuffer_convert – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 8de0091af93120290105ce7603fae5acff257b76
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688545"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert – třída

Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků do a z vyrovnávací paměti datového proudu bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Codecvt*|Omezující vlastnost [národního prostředí](../standard-library/locale-class.md) , která představuje objekt převodu.|
|*Elem*|Typ elementu s velkým znakem.|
|*Traits*|Vlastnosti přidružené k *elem*.|

## <a name="remarks"></a>Poznámky

Tato šablona třídy popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu `_Elem`, jejichž charakteristické znaky jsou popsány třídou `Traits`, do a z vyrovnávací paměti datového proudu typu `std::streambuf`.

Převod mezi sekvencí `Elem` hodnoty a vícebajtové sekvence je proveden pomocí objektu třídy `Codecvt<Elem, char, std::mbstate_t>`, který splňuje požadavky standardní omezující vlastnosti převodu kódu `std::codecvt<Elem, char, std::mbstate_t>`.

Objekt této šablony třídy ukládá:

- Ukazatel na svou podkladovou vyrovnávací paměť datového proudu

- Ukazatel na objekt přidělené konverze (který je uvolněn při [wbuffer_convert](../standard-library/wbuffer-convert-class.md)
