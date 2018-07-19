---
title: wbuffer_convert – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364ae6c544f58f09208cefeec9d3984de35120e1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965213"
---
# <a name="wbufferconvert-class"></a>wbuffer_convert – třída

Popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z vyrovnávací paměti datového proudu bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*codecvt –*|[Národní prostředí](../standard-library/locale-class.md) omezující vlastnost, která představuje objekt převodu.|
|*Elem*|Typ elementu širokého znaku.|
|*Osobnostní rysy*|Vlastnosti přidružené k *Elem*.|

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky typu `_Elem`, jehož vlastnosti znaků jsou popsány pomocí třídy `Traits`, do a z vyrovnávací paměti datového proudu bajtů typu `std::streambuf`.

Převod mezi sekvencí `Elem` hodnoty a vícebajtové sekvence se provádí pomocí objektu třídy `Codecvt<Elem, char, std::mbstate_t>`, který splňuje požadavky omezující vlastnost standardní převodu kódu `std::codecvt<Elem, char, std::mbstate_t>`.

Ukládá se objekt této třídy šablony:

- Ukazatel na jeho základní vyrovnávací paměť datového proudu bajtů

- Ukazatel na objekt přidělený převod (což je uvolněna při [wbuffer_convert –](../standard-library/wbuffer-convert-class.md)
