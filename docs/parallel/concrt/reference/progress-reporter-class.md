---
title: progress_reporter – třída
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: bd8f50a8c9829ff9de3e2412b89aa4de88d90db6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138776"
---
# <a name="progress_reporter-class"></a>progress_reporter – třída

Třída zpravodaj průběhu umožňuje vytváření sestav o průběhu konkrétního typu. Každý objekt progress_reporter je vázán na určitou asynchronní akci nebo operaci.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _ProgressType>
class progress_reporter;
```

### <a name="parameters"></a>Parametry

*_ProgressType*<br/>
Typ datové části pro každé oznámení o průběhu hlášené prostřednictvím zpravodajového procesu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[slouží](#report)|Odešle zprávu o průběhu asynchronní akci nebo operaci, na kterou je vázán tento přístavů průběhu.|

## <a name="remarks"></a>Poznámky

Tento typ je k dispozici jenom pro prostředí Windows Runtime aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`progress_reporter`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>progress_reporter

```cpp
progress_reporter();
```

## <a name="report"></a>slouží

Odešle zprávu o průběhu asynchronní akci nebo operaci, na kterou je vázán tento přístavů průběhu.

```cpp
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>Parametry

*počítává*<br/>
Datová část, která se má ohlásit pomocí oznámení o průběhu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
