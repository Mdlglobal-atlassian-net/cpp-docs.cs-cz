---
title: Exception – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ec1cfe2be7f6a2172b6624f15cb3dcde4f0ba3c2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957015"
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
