---
title: codecvt_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 1a32ba5e583fdb20118a3397f1ddb326302f2de1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459391"
---
# <a name="codecvtbase-class"></a>codecvt_base – třída

Základní třída pro třídu codecvt, která se používá k definování typu `result`výčtu, který se používá jako návratový typ pro členské funkce omezující vlastnosti pro indikaci výsledku převodu.

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

Třída popisuje výčet společný pro všechny specializace třídy template [codecvt](../standard-library/codecvt-class.md). Výsledek výčtu popisuje možné návratové hodnoty z [do_in](../standard-library/codecvt-class.md#do_in) nebo [do_out](../standard-library/codecvt-class.md#do_out):

- `ok`Pokud konverze mezi interním a externím kódováním znaků je úspěšná.

- `partial`Pokud cíl není dostatečně velký, aby převod mohl být úspěšný.

- `error`v případě, že je zdrojová sekvence nesprávně vytvořená.

- `noconv`Pokud funkce neprovede žádný převod.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
