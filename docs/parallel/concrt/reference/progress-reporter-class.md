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
ms.openlocfilehash: 5fc433beea560001badf919f55dbff45428ef876
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464854"
---
# <a name="progressreporter-class"></a>progress_reporter – třída

Třída zpravodaj pokroku umožňuje vykazování průběhu oznámení určitého typu. Každý objekt progress_reporter je vázán na konkrétní asynchronní akci nebo operaci.

## <a name="syntax"></a>Syntaxe

```
template<typename _ProgressType>
class progress_reporter;
```

#### <a name="parameters"></a>Parametry

*_ProgressType*<br/>
Typ datové části každého oznámení o pokroku vykázaného prostřednictvím.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Sestavy](#report)|Odešle zprávu o pokroku asynchronní akce nebo operace, ke kterému je vázán tento zpravodaj pokroku.|

## <a name="remarks"></a>Poznámky

Tento typ je pouze k dispozici pro aplikace Windows Runtime.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`progress_reporter`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> progress_reporter –

```
progress_reporter();
```

##  <a name="report"></a> Sestavy

Odešle zprávu o pokroku asynchronní akce nebo operace, ke kterému je vázán tento zpravodaj pokroku.

```
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Datové zprávy prostřednictvím oznámení postupu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
