---
title: Třída exception
ms.date: 11/04/2016
f1_keywords:
- exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 90906469e923d29dd886930bd36944e4292bd9cd
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246072"
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
