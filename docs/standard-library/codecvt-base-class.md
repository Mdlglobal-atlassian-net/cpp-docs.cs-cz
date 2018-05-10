---
title: codecvt_base – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_base
dev_langs:
- C++
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abe2a27a79705e9850df2c9fb54037278abd8cd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="codecvtbase-class"></a>codecvt_base – třída

Základní třída pro codecvt – třída, která se používá k definování typu výčtu označuje jako **výsledek**, použít jako návratový typ pro členské funkce omezující vlastnost udávajících výsledek převodu z.

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

Třída popisuje výčet společné pro všechny specializací třídy šablony [codecvt –](../standard-library/codecvt-class.md). Výsledek výčtu popisuje možné vrácené hodnoty z [do_in –](../standard-library/codecvt-class.md#do_in) nebo [do_out –](../standard-library/codecvt-class.md#do_out):

- **OK** Pokud převod mezi kódování znaků interních a externích úspěšné.

- **částečné** Pokud cíl není dostatečně velký pro převod úspěšný.

- **Chyba** vytvořen. Pokud zdrojové sekvence je chybný.

- **noconv** Pokud funkce provádí žádný převod.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
