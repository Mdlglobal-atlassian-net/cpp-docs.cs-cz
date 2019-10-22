---
title: codecvt_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6fca9b2130407b165a7a7bfb1fb2a9ec81774e20
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689888"
---
# <a name="codecvt_base-class"></a>codecvt_base – třída

Základní třída pro třídu codecvt, která se používá k definování typu výčtu označovaného jako `result`, použit jako návratový typ pro členské funkce omezující podmínky k indikaci výsledku převodu.

## <a name="syntax"></a>Syntaxe

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>Poznámky

Třída popisuje výčet společný pro všechny specializace šablony třídy [codecvt](../standard-library/codecvt-class.md). Výsledek výčtu popisuje možné návratové hodnoty z [do_in](../standard-library/codecvt-class.md#do_in) nebo [do_out](../standard-library/codecvt-class.md#do_out):

- `ok`, zda převod mezi interním a externím kódováním znaků je úspěšný.

- `partial`, pokud cíl není dostatečně velký, aby byl převod úspěšný.

- `error`, pokud je zdrojová sekvence nesprávně vytvořená.

- `noconv`, pokud funkce neprovede žádný převod.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
