---
title: threadprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9313934744f6eae66736f25b0d0b8592743cf12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376977"
---
# <a name="threadprivate"></a>threadprivate

Určuje, že proměnná je privátní pro vlákno.

## <a name="syntax"></a>Syntaxe

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Čárkou oddělený seznam proměnných, které chcete označit jako soukromé ve vlákně. `var` musí být globální nebo obor názvů rozsahem proměnné nebo statické místní proměnné.

## <a name="remarks"></a>Poznámky

`threadprivate` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.7.1 threadprivate – direktiva](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

`threadprivate` Podle směrnice [vlákno](../../../cpp/thread.md) `__declspec` atribut; omezení **__declspec(thread)** platí pro `threadprivate`.

Nemůžete použít `threadprivate` v žádné knihovny DLL, která se načtou prostřednictvím [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175).  To zahrnuje knihovny DLL, které načítají s [/delayload (Import odloženého načtení)](../../../build/reference/delayload-delay-load-import.md), který také používá **LoadLibrary**.

Můžete použít `threadprivate` v knihovně DLL, která je staticky načtená při spouštění procesu.

Protože `threadprivate` vychází **__declspec(thread)**, `threadprivate` proměnné budou existovat v jakékoli vlákno spuštění v procesu, nejen vlákna, které jsou součástí týmu vlákna vytvořený službou paralelní oblasti.  Toto je podrobnosti implementace, které chcete mít na paměti, protože jste si všimnout, například konstruktory pro `threadprivate` uživatelem definovaného typu vyvoláno více často, než očekáváte.

A `threadprivate` proměnnou typu destructable nemusí mít jeho destruktor volá.  Příklad:

```
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Uživatelé nemají žádnou kontrolu, když se ukončí vlákna tvořící paralelní oblasti.  Pokud tato vlákna při ukončení procesu, vlákna nebudete nijak upozorněni o ukončení procesu a destruktor se nebude volat pro `threaded_var` v libovolném vlákně kromě toho, který ukončí (tady, primární vlákno).  Takže kód by neměl spolehnout na řádné zničení `threadprivate` proměnné.

## <a name="example"></a>Příklad

Pro ukázkový používání `threadprivate`, naleznete v tématu [privátní](../../../parallel/openmp/reference/private-openmp.md).

## <a name="see-also"></a>Viz také

[Direktivy](../../../parallel/openmp/reference/openmp-directives.md)