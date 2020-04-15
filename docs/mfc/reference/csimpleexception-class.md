---
title: CSimpleException – třída
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318361"
---
# <a name="csimpleexception-class"></a>CSimpleException – třída

Tato třída je základní třídou pro výjimky knihovny MFC kritické pro prostředky.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Obsahuje text o chybě, ke které došlo.|

## <a name="remarks"></a>Poznámky

`CSimpleException`je základní třída pro výjimky knihovny MFC kritické pro prostředky a zpracovává vlastnictví a inicializaci chybové zprávy. Následující třídy `CSimpleException` používají jako svou základní třídu:

|||
|-|-|
|[CMemoryException – třída](../../mfc/reference/cmemoryexception-class.md)|Výjimka nedostatku paměti|
|[CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)|Požadavky na nepodporovanou operaci|
|[CResourceException – třída](../../mfc/reference/cresourceexception-class.md)|Prostředek systému Windows nebyl nalezen nebo není kreatable|
|[Třída CUserException](../../mfc/reference/cuserexception-class.md)|Výjimka, která označuje, že prostředek nebyl nalezen.|
|[CInvalidArgException – třída](../../mfc/reference/cinvalidargexception-class.md)|Výjimka, která označuje neplatný argument|

Protože `CSimpleException` je abstraktní základní třída, `CSimpleException` nelze deklarovat objekt přímo. Místo toho je nutné deklarovat odvozené objekty, jako jsou ty v předchozí tabulce. Pokud deklarujete vlastní odvozenou třídu, použijte předchozí třídy jako model.

Další informace naleznete v tématu [CException Class](../../mfc/reference/cexception-class.md) a [Exception Handling (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>CSimpleException::CSimpleException

Konstruktor

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*bAutoDelete*<br/>
Zadejte hodnotu TRUE, pokud byla na haldě přidělena paměť `CSimpleException` pro objekt. To způsobí, `CSimpleException` že objekt, `Delete` který má být odstraněn, když je volána členská funkce k odstranění výjimky. Zadejte hodnotu NEPRAVDA, `CSimpleException` pokud je objekt v zásobníku nebo je globálním objektem. V takovém případě `CSimpleException` nebude objekt odstraněn `Delete` při volání členské funkce.

### <a name="remarks"></a>Poznámky

Za normálních okolností by nikdy nutné volat tento konstruktor přímo. Funkce, která vyvolá výjimku by měla `CException`vytvořit instanci odvozené třídy a volat jeho konstruktor, nebo by měla použít jednu z funkcí mfc throw, jako je například [AfxThrowFileException](exception-processing.md#afxthrowfileexception), k vyvolání předdefinovaného typu.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>CSimpleException::GetErrorMessage

Volání této členské funkce poskytnout text o chybě, ke které došlo.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parametry

*chyba lpsz*<br/>
Ukazatel na vyrovnávací paměť, která obdrží chybovou zprávu.

*nChyba*<br/>
Maximální počet znaků, které může vyrovnávací paměť obsahovat, včetně zakončení NULL.

*pnHelpContext*<br/>
Adresa UINT, který obdrží ID kontextu nápovědy. Pokud null, žádné ID bude vrácena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; v opačném případě 0, pokud není k dispozici žádný text chybové zprávy.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Zpracování výjimek](../../mfc/exception-handling-in-mfc.md)
