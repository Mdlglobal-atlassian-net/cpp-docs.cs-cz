---
title: Třída Exception | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff6bc46fb8776de5f93b623b98f87513e710c603
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="exception-class"></a>Třída exception

Třída slouží jako základní třída pro všechny výjimky vydané určité výrazy a standardní knihovny C++.

## <a name="syntax"></a>Syntaxe

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };
```

## <a name="remarks"></a>Poznámky

Konkrétně tato základní třída je kořenem standardní výjimka tříd definovaných v [ \<stdexcept – >](../standard-library/stdexcept.md). C řetězce hodnoty vrácené `what` vlevo je neurčené výchozí konstruktor, ale může být konstruktory pro určité odvozené třídy definována jako řetězec definované implementací C. Žádná z členské funkce throw jakékoli výjimky.

`int` Parametr umožňuje určit, že by měla být přidělená není dostatek paměti. Hodnota `int` je ignorována.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` a `exception(const char* const &message, int)` jsou rozšíření Microsoft pro standardní knihovna C++.

## <a name="example"></a>Příklad

Příklady použití třídy standardní výjimek, které dědí od `exception` naleznete v některé z tříd definovaných v [ \<stdexcept – >](../standard-library/stdexcept.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimka >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
