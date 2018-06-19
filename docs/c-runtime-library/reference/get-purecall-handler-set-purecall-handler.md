---
title: _get_purecall_handler, _set_purecall_handler – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
dev_langs:
- C++
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dca104d04546786a361c63461e502f7aa8b6127
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400272"
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler

Získá nebo nastaví obslužnou rutinu chyby pro volání čistý virtuální funkce.

## <a name="syntax"></a>Syntaxe

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parametry

*Funkce*<br/>
Funkce, která se má volat při volání čistou virtuální funkci. A **_purecall_handler** funkce musí mít typ vrácené hodnoty void.

## <a name="return-value"></a>Návratová hodnota

Předchozí **_purecall_handler**. Vrátí **nullptr** Pokud se žádná předchozí obslužná rutina.

## <a name="remarks"></a>Poznámky

**_Get_purecall_handler** a **_set_purecall_handler –** funkce jsou specifické pro společnost Microsoft a platí pouze pro C++ – kód.

Volání čistou virtuální funkci se o chybu, protože nemá žádné implementace. Ve výchozím nastavení kompilátor generuje kód pro vyvolání funkce obslužné rutiny k chybě při volání čistou virtuální funkci, která ukončí program. Můžete nainstalovat funkci obslužné rutiny vlastní chyby pro volání čistou virtuální funkci, je pro ladění nebo účely vytváření sestav zachytit. Pokud chcete používat vlastní obslužnou rutinu chyby, vytvořte funkci, která má **_purecall_handler** podpis, pak použít **_set_purecall_handler –** Chcete-li obslužná rutina aktuální.

Protože je pouze jedna **_purecall_handler** pro každý proces, při volání **_set_purecall_handler –** ji okamžitě ovlivňuje všechna vlákna. Poslední volající na jakékoli vlákno nastaví obslužnou rutinu.

Chcete-li obnovit výchozí chování, volejte **_set_purecall_handler –** pomocí **nullptr** argument.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler –**|\<cstdlib – > nebo \<stdlib.h >|

Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>Viz také

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
