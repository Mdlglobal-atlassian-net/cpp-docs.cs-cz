---
title: _get_purecall_handler, _set_purecall_handler
ms.date: 11/04/2016
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
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 0009b4bc1c7bf70bd84b9a82ecdc8643789e8164
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646355"
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler

Získá nebo nastaví obslužnou rutinu chyby pro volání čistě virtuální funkce.

## <a name="syntax"></a>Syntaxe

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parametry

*– funkce*<br/>
Funkce, která se má volat při volání čistě virtuální funkce. A **_purecall_handler** funkce musí mít typ vrácené hodnoty void.

## <a name="return-value"></a>Návratová hodnota

Předchozí **_purecall_handler**. Vrátí **nullptr** Pokud žádná předchozí obslužnou rutinou.

## <a name="remarks"></a>Poznámky

**_Get_purecall_handler** a **_set_purecall_handler –** funkce jsou specifické pro společnost Microsoft a platí pouze pro kód jazyka C++.

Volání čistě virtuální funkce se o chybu, protože nemá žádnou implementaci. Ve výchozím nastavení kompilátor vygeneruje kód pro vyvolat funkci obslužné rutiny k chybě při volání čistě virtuální funkce, která ukončí program. Můžete nainstalovat vlastní funkci obslužné rutiny chyby pro volání čistě virtuální funkce, je pro ladění nebo pro účely vykazování zachytit. Pokud chcete použít vlastní obslužnou rutinu chyb, vytvořte funkci, která má **_purecall_handler** podpis, pak použít **_set_purecall_handler –** k němu aktuální obslužné rutiny.

Protože je jen jeden **_purecall_handler** pro každý proces, při volání **_set_purecall_handler –** okamžitě ovlivní všechna vlákna. Poslední volající v libovolném vlákně nastaví obslužnou rutinu.

Chcete-li obnovit výchozí chování, zavolejte **_set_purecall_handler –** pomocí **nullptr** argument.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler –**|\<cstdlib – > nebo \<stdlib.h >|

Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
