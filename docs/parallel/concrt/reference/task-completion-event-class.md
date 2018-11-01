---
title: task_completion_event – třída
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: ae4cce94dd7b36cebadea5f6d05890d979cce474
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498953"
---
# <a name="taskcompletionevent-class"></a>task_completion_event – třída

`task_completion_event` Třída umožňuje zpoždění spuštění úlohy, dokud není splněna podmínka, nebo spuštění úlohy jako odpověď na vnější události.

## <a name="syntax"></a>Syntaxe

```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

#### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ výsledku této `task_completion_event` třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_completion_event](#ctor)|Vytvoří `task_completion_event` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[set](#set)|Přetíženo. Nastaví událost dokončení úkolu.|
|[set_exception](#set_exception)|Přetíženo. Rozšíří výjimku pro všechny úkoly spojené s touto událostí.|

## <a name="remarks"></a>Poznámky

Použijte úlohu vytvořenou z události dokončení úkolu když vaše situace vyžaduje vytvoření úlohy, která bude dokončena, a tím bude její pokračování naplánováno ke spuštění v určitém okamžiku v budoucnu. `task_completion_event` Musí být stejného typu jako úkol vytvoříte a volání metody set na událost dokončení úkolu s hodnotou tohoto typu způsobí dokončení přidruženého úkolu a poskytne tuto hodnotu v důsledku jeho pokračování.

Pokud událost dokončení úlohy není signalizována, všechny úlohy z ní vytvořené budou zrušeny při její destrukci.

`task_completion_event` se chová jako inteligentní ukazatel a musí být předán podle hodnoty.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task_completion_event`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks.h

**Namespace:** souběžnosti

##  <a name="set"></a> Nastavit

Nastaví událost dokončení úkolu.

```
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Parametry

*_Result*<br/>
Výsledek, který má tato událost nastavit.

### <a name="return-value"></a>Návratová hodnota

Metoda vrátí **true** Pokud bylo nastavení události úspěšné. Vrátí **false** -li událost již nastavena.

### <a name="remarks"></a>Poznámky

Za přítomnosti více nebo souběžných volání `set`, bude úspěšné pouze první volání a jeho výsledek (pokud existují) budou uložena v události dokončení úkolu. Zbývající sady jsou ignorovány a metoda vrátí hodnotu false. Při nastavení události dokončení úkolu budou všechny úkoly vytvořené z, že události okamžitě dokončeny a její pokračování, pokud existuje, bude naplánováno. Úloha dokončení objekty, které mají `_ResultType` jiné než **void** předají hodnotu svým následovníkům.

##  <a name="set_exception"></a> set_exception

Rozšíří výjimku pro všechny úkoly spojené s touto událostí.

```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Parametry

*_E*<br/>
Typ výjimky.

*_Except*<br/>
Výjimka k nastavení.

*_ExceptionPtr*<br/>
Výjimka ukazatel k nastavení.

### <a name="return-value"></a>Návratová hodnota

##  <a name="ctor"></a> task_completion_event –

Vytvoří `task_completion_event` objektu.

```
task_completion_event();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
