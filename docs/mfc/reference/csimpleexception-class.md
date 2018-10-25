---
title: Csimpleexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ab21338eabe2e432189ccf8a5aae3432005657d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083214"
---
# <a name="csimpleexception-class"></a>Csimpleexception – třída

Tato třída je základní třída pro výjimky kritických zdrojů MFC.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Poskytuje text o chybu, že došlo k chybě.|

## <a name="remarks"></a>Poznámky

`CSimpleException` Základní třída pro výjimky kritických zdrojů MFC a zpracovává vlastnictví a inicializace chybovou zprávu. Následující třídy použijte `CSimpleException` jako své základní třídy:

|||
|-|-|
|[CMemoryException – třída](../../mfc/reference/cmemoryexception-class.md)|Výjimka mimo z důvodu nedostatku paměti|
|[CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)|Žádosti o nepodporovanou operaci|
|[CResourceException – třída](../../mfc/reference/cresourceexception-class.md)|Windows prostředek nebyl nalezen nebo není možné vytvořit|
|[CUserException – třída](../../mfc/reference/cuserexception-class.md)|Výjimka, která určuje prostředek se nenašel.|
|[CInvalidArgException – třída](../../mfc/reference/cinvalidargexception-class.md)|Výjimka, která určuje neplatný argument.|

Protože `CSimpleException` je abstraktní základní třída, nelze deklarovat `CSimpleException` objektu přímo. Místo toho je třeba deklarovat odvozené objekty, jako jsou ty v předchozí tabulce. Pokud deklarujete odvozené třídy, použijte jako model předchozí třídy.

Další informace najdete v tématu [cexception – třída](../../mfc/reference/cexception-class.md) tématu a [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException

Konstruktor

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*bAutoDelete*<br/>
Zadejte hodnotu PRAVDA, pokud paměť pro `CSimpleException` objekt byl přidělen na haldě. To způsobí, že `CSimpleException` objektu, který chcete odstranit, když `Delete` členská funkce je volána k odstranění výjimku. Zadejte hodnotu FALSE, pokud `CSimpleException` objekt v zásobníku nebo je globální objekt. V tomto případě `CSimpleException` objektů nebudou odstraněny při `Delete` členská funkce je volána.

### <a name="remarks"></a>Poznámky

Je třeba obvykle nikdy přímo volání tohoto konstruktoru. Funkce, která vyvolá výjimku, by měl vytvořit instanci `CException`-odvozené třídy a volání konstruktoru, nebo použijte jedno z knihovny MFC vyvoláním funkce, jako například [afxthrowfileexception –](exception-processing.md#afxthrowfileexception), vyvolání předdefinovaný typ.

##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage

Voláním této funkce člena zadejte text o chybu, že došlo k chybě.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
Ukazatel do vyrovnávací paměti, která se zobrazí chybová zpráva.

*nMaxError*<br/>
Maximální počet znaků, které může obsahovat vyrovnávací paměti, včetně ukončovacího znaku NULL.

*pnHelpContext*<br/>
Adresa UINT, která bude dostávat ID kontextové nápovědy Pokud má hodnotu NULL, vrátí se žádné ID.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; v opačném případě 0, pokud žádná chyba text zprávy je k dispozici.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Zpracování výjimek](../../mfc/exception-handling-in-mfc.md)

