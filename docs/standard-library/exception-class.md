---
title: Třída exception
ms.date: 11/04/2016
f1_keywords:
- exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 009ef74d810976eb9f054b45e388ceb0fe612b2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521024"
---
# <a name="exception-class"></a>Třída exception

Tato třída slouží jako základní třída pro všechny výjimky vyvolané některými výrazy a standardní knihovny C++.

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

Konkrétně tato základní třída je kořenem standardní výjimka tříd definovaných v [ \<stdexcept – >](../standard-library/stdexcept.md). Hodnota vrácený řetězec jazyka C `what` nebyl zadán pomocí výchozího konstruktoru, ale může být definovaná jako řetězec definovanou implementací jazyka C pomocí konstruktorů určitých odvozených tříd. Žádná z členské funkce generovat žádné výjimky.

**Int** parametrů můžete zadat, že by měla být přidělená žádná paměť. Hodnota **int** se ignoruje.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` a `exception(const char* const &message, int)` jsou rozšíření Microsoft pro standardní knihovny C++.

## <a name="example"></a>Příklad

Příklady použití, které dědí z třídy standardní výjimka `exception` třídy, naleznete v některém z tříd definovaných v [ \<stdexcept – >](../standard-library/stdexcept.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimky >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
