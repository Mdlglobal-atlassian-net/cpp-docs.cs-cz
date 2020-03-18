---
title: Třída exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 5bef8190889ae00298760ea395fb524f557c2be2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446826"
---
# <a name="exception-class"></a>Třída exception

Třída slouží jako základní třída pro všechny výjimky vyvolané některými výrazy a C++ standardní knihovnou.

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

Konkrétně tato základní třída je kořenem standardních tříd výjimek definovaných v [\<stdexcept >](../standard-library/stdexcept.md). Hodnota řetězce C vrácená funkcí `what` není určena výchozím konstruktorem, ale může být definována konstruktory pro určité odvozené třídy jako řetězec jazyka C definované implementací. Žádná z členských funkcí nevyvolá žádné výjimky.

Parametr **int** umožňuje určit, že by neměla být přidělena žádná paměť. Hodnota **int** je ignorována.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` a `exception(const char* const &message, int)` jsou rozšířeními společnosti Microsoft pro C++ standardní knihovnu.

## <a name="example"></a>Příklad

Příklady použití třídy standardní výjimky, které dědí z třídy `exception`, naleznete v libovolné třídě definované v [\<stdexcept >](../standard-library/stdexcept.md).
