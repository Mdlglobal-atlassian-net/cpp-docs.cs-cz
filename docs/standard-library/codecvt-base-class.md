---
title: codecvt_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6f957c39f9c78fd182b7ba2a14bdab7f27db56ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405297"
---
# <a name="codecvtbase-class"></a>codecvt_base – třída

Základní třída pro třídu codecvt, která slouží k definování typu výčtu uvedené jako `result`, která se používá jako návratový typ členských funkcí omezující vlastnosti k určení výsledku převodu.

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

Tato třída popisuje společné pro všechny specializace šablony třídy výčtu [codecvt](../standard-library/codecvt-class.md). Popisuje výsledek výčet možných vrácených hodnot z [do_in](../standard-library/codecvt-class.md#do_in) nebo [do_out](../standard-library/codecvt-class.md#do_out):

- `ok` Pokud bude úspěšné převodu mezi interním a externím kódováním znaků.

- `partial` Pokud cíl není dostatečně velký pro úspěšný převod.

- `error` Pokud je zdrojové sekvence výplně tvar.

- `noconv` Pokud funkce provádí převod.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
