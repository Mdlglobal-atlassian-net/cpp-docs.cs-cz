---
title: CFileTimeSpan – třída
description: Aktivní knihovna šablon (ATL) a Třída Knihovny Microsoft Foundation (MFC) CFileTimeSpan třída spravuje časové intervaly v jednotkách FILETIME.
ms.date: 01/10/2020
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317857"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan – třída

Tato třída poskytuje metody pro správu relativních hodnot data a času přidružených k souboru.

## <a name="syntax"></a>Syntaxe

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejní konstruktéři

|Name (Název)|Popis|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Volání této metody načíst časový `CFileTimeSpan` rozsah z objektu.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Volání této metody nastavit časový rozsah `CFileTimeSpan` objektu.|

### <a name="public-operators"></a>Veřejní provozovatelé

|Name (Název)|Popis|
|----------|-----------------|
|[CFileTimeSpan::operátor -](#operator_-)|Provede odčítání `CFileTimeSpan` objektu.|
|[CFileTimeSpan::operátor !=](#operator_neq)|Porovná dva `CFileTimeSpan` objekty pro nerovnost.|
|[CFileTimeSpan::operátor +](#operator_add)|Provádí sčítání `CFileTimeSpan` na objekt.|
|[CFileTimeSpan::operátor +=](#operator_add_eq)|Provede sčítání `CFileTimeSpan` objektu a přiřadí výsledek aktuálnímu objektu.|
|[CFileTimeSpan::operátor&lt;](#operator_lt)|Porovná dva `CFileTimeSpan` objekty k určení menší.|
|[CFileTimeSpan::operátor&lt;=](#operator_lt_eq)|Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo menší.|
|[CFileTimeSpan::operátor =](#operator_eq)|Operátor přiřazení.|
|[CFileTimeSpan::operátor -=](#operator_-_eq)|Provede odčítání `CFileTimeSpan` objektu a přiřadí výsledek aktuálnímu objektu.|
|[CFileTimeSpan::operátor ==](#operator_eq_eq)|Porovná dva `CFileTimeSpan` objekty rovnosti.|
|[CFileTimeSpan::operátor&gt;](#operator_gt)|Porovná dva `CFileTimeSpan` objekty k určení větší.|
|[CFileTimeSpan::operátor&gt;=](#operator_gt_eq)|Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo větší.|

## <a name="remarks"></a>Poznámky

Třída `CFileTimeSpan` poskytuje metody pro zpracování relativních období času v jednotkách, které systém souborů používá. Tyto jednotky se často používají při operacích se soubory, například při vytvoření, posledním přístupu k souboru nebo naposledy změně. Metody této třídy se často používají ve spojení s objekty [třídy CFileTime.](../../atl-mfc-shared/reference/cfiletime-class.md)

## <a name="example"></a>Příklad

Viz příklad [cfiletime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Konstruktor

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Existující objekt `CFileTimeSpan`.

*nSpan*\
Časové období v jednotkách FILETIME.

### <a name="remarks"></a>Poznámky

Objekt `CFileTimeSpan` lze vytvořit pomocí `CFileTimeSpan` existujícího objektu nebo vyjádřenjako 64bitová hodnota v jednotkách FILETIME 100 nanosekund. Další informace naleznete v tématu [CFileTime](cfiletime-class.md). Výchozí konstruktor nastaví časové rozpětí na 0.

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

Volání této metody načíst časový `CFileTimeSpan` rozsah z objektu.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí časový rozsah v jednotkách FILETIME 100 nanosekund. Další informace naleznete v tématu [CFileTime](cfiletime-class.md).

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>CFileTimeSpan::operátor -

Provede odčítání `CFileTimeSpan` objektu.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTimeSpan` objekt představující výsledek rozdílu mezi dvěma časovými rozpětími.

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>CFileTimeSpan::operátor !=

Porovná dva `CFileTimeSpan` objekty pro nerovnost.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt, `CFileTimeSpan` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se porovnávaná položka nerovná objektu; `CFileTimeSpan` jinak FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>CFileTimeSpan::operátor +

Provádí sčítání `CFileTimeSpan` na objekt.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTimeSpan` objekt obsahující součet dvou časových rozpětí.

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>CFileTimeSpan::operátor +=

Provede sčítání `CFileTimeSpan` objektu a přiřadí výsledek aktuálnímu objektu.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt obsahující součet dvou časových rozpětí.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>CFileTimeSpan::operátor&lt;

Porovná dva `CFileTimeSpan` objekty k určení menší.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt, `CFileTimeSpan` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší (to znamená, že představuje kratší časové období) než druhý, jinak NEPRAVDA.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>CFileTimeSpan::operátor&lt;=

Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo menší.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt, `CFileTimeSpan` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší než (to znamená, že představuje kratší časové období) nebo rovna druhému, jinak NEPRAVDA.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>CFileTimeSpan::operátor =

Operátor přiřazení.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt.

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>CFileTimeSpan::operátor -=

Provede odčítání `CFileTimeSpan` objektu a přiřadí výsledek aktuálnímu objektu.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>CFileTimeSpan::operátor ==

Porovná dva `CFileTimeSpan` objekty rovnosti.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt, `CFileTimeSpan` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou objekty stejné, jinak NEPRAVDA.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>CFileTimeSpan::operátor&gt;

Porovná dva `CFileTimeSpan` objekty k určení větší.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt, `CFileTimeSpan` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt větší než (to znamená delší časové období) než druhý, jinak NEPRAVDA.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>CFileTimeSpan::operátor&gt;=

Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo větší.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Objekt, `CFileTimeSpan` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt větší než (to znamená delší časové období) nebo rovna druhému, jinak NEPRAVDA.

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Volání této metody nastavit časový rozsah `CFileTimeSpan` objektu.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*\
Nová hodnota pro časové rozpětí ve 100nanosekundových jednotkách FILETIME. Další informace naleznete v tématu [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Viz také

[ČAS SOUBORU](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[Třída CFileTime](cfiletime-class.md)\
[Graf hierarchie](../../mfc/hierarchy-chart.md)\
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
