---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation: api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs: C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 630b8a5160eaa808c12c16ec8dd45a96a621b7bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function
Spravuje rutiny, která se má volat v době ukončení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _initialize_onexit_table(  
    _onexit_table_t* table  
    );  
  
int _register_onexit_function(  
    _onexit_table_t* table,  
    _onexit_t        function  
    );  
  
int _execute_onexit_table(  
    _onexit_table_t* table  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 [inout]`table`  
 Ukazatel do funkce tabulky při výstupu.  
  
 [v]`function`  
 Ukazatel na funkci, kterou chcete přidat do tabulky funkce při výstupu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu 0. Jinak vrátí zápornou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce jsou podrobnosti implementace infrastruktury použitá k podpoře C runtime a nelze volat přímo z vašeho kódu. C runtime používá *onexit – funkce tabulky* představují pořadí registrované ve volání funkce `atexit`, `at_quick_exit`, a `_onexit`. Datová struktura onexit – funkce tabulky je podrobností neprůhledného implementace C Runtime; pořadí a význam svých členů data mohou změnit. By neměl být prověřovány externí kódem.  
  
 `_initialize_onexit_table` Funkce inicializuje onexit – funkce tabulka, která se počáteční hodnoty.  Tato funkce musí být volána, než tabulka funkce onexit – je předán buď `_register_onexit_function` nebo `_execute_onexit_table`.  
  
 `_register_onexit_function` Funkce přidá funkci na konec tabulky onexit – funkce.  
  
 `_execute_onexit_table` Funkce provede všechny funkce v tabulce onexit – funkce, vymaže v tabulce a vrátí. Po volání `_execute_onexit_table`, v tabulce je ve stavu neplatné; musí být znovu inicializovány voláním `_initialize_onexit_table` předtím, než se znovu použít.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h >|  
  
 `_initialize_onexit_table`, `_register_onexit_function`, A `_execute_onexit_table` funkce se konkrétní společnosti Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [AtExit](../c-runtime-library/reference/atexit.md)   
 [ukončení, _exit –, _exit –](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit –, _onexit_m –](../c-runtime-library/reference/onexit-onexit-m.md)