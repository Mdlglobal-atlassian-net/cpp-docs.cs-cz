---
title: threadprivate | Microsoft Docs
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
ms.openlocfilehash: e7e7edaa36f929750087e3c81f42204ff20e9f62
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692909"
---
# <a name="threadprivate"></a>threadprivate
Určuje, že je na vlákno soukromé proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp threadprivate(var)  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `var`  
 Seznam proměnných, které chcete nastavit jako soukromé na vlákno oddělených čárkami. `var` musí být buď globální nebo obor názvů obor proměnné nebo místní statické proměnné.  
  
## <a name="remarks"></a>Poznámky  
 `threadprivate` – Direktiva podporuje žádné OpenMP – klauzule.  
  
 Další informace najdete v tématu [2.7.1 threadprivate – direktiva](../../../parallel/openmp/2-7-1-threadprivate-directive.md).  
  
 `threadprivate` – Direktiva je založena na [vlákno](../../../cpp/thread.md) `__declspec` atribut; omezení **__declspec(thread)** platí pro `threadprivate`.  
  
 Nemůžete použít `threadprivate` v jakékoli knihovnu DLL, kterou bude načten prostřednictvím [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175).  To zahrnuje knihovny DLL, které jsou načtené s [/DELAYLOAD (Import odloženého načtení)](../../../build/reference/delayload-delay-load-import.md), který také používá **LoadLibrary**.  
  
 Můžete použít `threadprivate` v knihovně DLL, která je staticky načtena při spuštění procesu.  
  
 Protože `threadprivate` je založena na **__declspec(thread)**, `threadprivate` proměnné budou existovat v jakékoli vlákno spuštěna v procesu, ne jenom vláken, které jsou součástí seskupení adaptérů vlákno vytvořený službou paralelní oblast.  Toto je podrobností implementace, kterou chcete mít na paměti, vzhledem k tomu může dojít, například konstruktory pro `threadprivate` uživatelem definovaný typ volat další často pak očekává.  
  
 A `threadprivate` proměnné destructable typu není zaručena tak, aby měl jeho destruktor volat.  Příklad:  
  
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
  
 Uživatelé nemají žádnou kontrolu, když bude ukončen vláken tvořící paralelní oblast.  Pokud tyto vláken existovat, pokud proces bude ukončen, vláken nebude upozorněn na ukončení procesu a destruktoru nebude volána pro `threaded_var` na jakékoli vlákno kromě toho, který ukončí (tady, primární vlákno).  Takže kód neměli spoléhat na správné zničení `threadprivate` proměnné.  
  
## <a name="example"></a>Příklad  
 Pro ukázkové použití `threadprivate`, najdete v části [privátní](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Viz také  
 [Direktivy](../../../parallel/openmp/reference/openmp-directives.md)