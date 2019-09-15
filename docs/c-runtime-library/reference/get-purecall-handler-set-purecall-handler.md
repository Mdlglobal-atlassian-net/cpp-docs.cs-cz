---
title: _get_purecall_handler, _set_purecall_handler
ms.date: 11/04/2016
api_name:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 73fc2ffe5cd4ed65c8695432b53816090bbc5f8e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955679"
---
# <a name="_get_purecall_handler-_set_purecall_handler"></a>_get_purecall_handler, _set_purecall_handler

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

*slouží*<br/>
Funkce, která se má volat při volání čistě virtuální funkce Funkce **_purecall_handler** musí mít návratový typ void.

## <a name="return-value"></a>Návratová hodnota

Předchozí **_purecall_handler** Vrátí **nullptr** , pokud neexistuje předchozí obslužná rutina.

## <a name="remarks"></a>Poznámky

Funkce **_get_purecall_handler** a **_set_purecall_handler** jsou specifické pro společnost Microsoft a platí pouze pro C++ kód.

Volání čistě virtuální funkce je chyba, protože nemá žádnou implementaci. Ve výchozím nastavení kompilátor generuje kód pro vyvolání funkce obslužné rutiny chyb při volání čistě virtuální funkce, která program ukončí. Můžete nainstalovat vlastní funkci obslužné rutiny chyb pro volání čistě virtuální funkce, abyste je mohli zachytit pro účely ladění nebo generování sestav. Chcete-li použít vlastní obslužnou rutinu chyb, vytvořte funkci, která má signaturu **_purecall_handler** , pak pomocí **_set_purecall_handler** ji nastavte na aktuální obslužnou rutinu.

Vzhledem k tomu, že pro každý proces existuje pouze jeden **_purecall_handler** , při volání **_set_purecall_handler** IT okamžitě ovlivní všechna vlákna. Poslední volající v jakémkoli vlákně nastaví obslužnou rutinu.

Chcete-li obnovit výchozí chování, zavolejte **_set_purecall_handler** pomocí argumentu **nullptr** .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler**|\<cstdlib > nebo \<Stdlib. h >|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
