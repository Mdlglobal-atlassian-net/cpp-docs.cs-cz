---
title: CStrBufT – třída
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 84c67aa8ea819f420368a72a2374f800f3d89055
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317650"
---
# <a name="cstrbuft-class"></a>CStrBufT – třída

Tato třída poskytuje automatické `GetBuffer` vyčištění `ReleaseBuffer` prostředků pro `CStringT` a volání existujícího objektu.

## <a name="syntax"></a>Syntaxe

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parametry

*TChartype*<br/>
Typ znaku `CStrBufT` třídy. Může to být jedna z následujících možností:

- **char** (pro řetězce znaků ANSI)

- **wchar_t** (pro řetězce znaků Unicode)

- TCHAR (pro řetězce znaků ANSI i Unicode)

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|PCXSTR|Ukazatel na konstantní řetězec.|
|PXSTR|Ukazatel na řetězec.|
|`StringType`|Typ řetězce, jehož vyrovnávací paměť má být manipulováno specializace této šablony třídy.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Konstruktor pro objekt vyrovnávací paměti řetězce.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Nastaví délku vyrovnávací paměti znaků přidruženého objektu řetězce.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CStrBufT::operátor PCXSTR](#operator_pcxstr)|Načte ukazatel **const** do vyrovnávací paměti znaků přidruženého objektu řetězce.|
|[CStrBufT::operátor PXSTR](#operator_pxstr)|Načte ukazatel na vyrovnávací paměť znaků přidruženého objektu řetězce.|

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Automaticky určete novou délku řetězce při uvolnění.|
|[CStrBufT::SET_LENGTH](#set_length)|Nastavení délky objektu řetězce v čase GetBuffer|

## <a name="remarks"></a>Poznámky

Tato třída se používá jako obálka třídy pro nahrazení volání [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a `ReleaseBuffer` [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)nebo [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) a .

Primárně navržen jako pomocná `CStrBufT` třída, poskytuje pohodlný způsob, jak pro vývojáře pracovat s vyrovnávací paměť `ReleaseBuffer`znaků objektu řetězce bez obav o tom, jak a kdy volat . To je možné, protože objekt obálky přirozeně přejde mimo rozsah v případě výjimky nebo více cest kódu ukončení; způsobuje jeho destruktor uvolnit prostředek řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT::AUTO_LENGTH

Automaticky určete novou délku řetězce při uvolnění.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Poznámky

Automaticky určete novou délku řetězce při uvolnění. Řetězec musí být ukončen a null.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

Vytvoří objekt vyrovnávací paměti.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Objekt řetězce přidružený k vyrovnávací paměti. Obvykle bude vývojář používat předdefinované typedefs `CStrBuf` (VariantTCHAR), `CStrBufA` **(char** `CStrBufW` variant) a (**wchar_t** varianta).

*nMinDélka*<br/>
Minimální délka vyrovnávací paměti znaků.

*dwFlags*<br/>
Určuje, zda je délka řetězce určena automaticky. Může to být jedna z následujících možností:

- AUTO_LENGTH Délka řetězce je automaticky určena při [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) je volána. Řetězec musí být ukončen a null. Výchozí hodnota.

- SET_LENGTH Délka řetězce je nastavena při [csimplestringt::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) je volána.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměť řetězce pro přidružený objekt řetězce. Během výstavby [cSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) nebo [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) se nazývá.

Všimněte si, že konstruktor kopie je **soukromý**.

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::operátor PCXSTR

Přímo přistupuje k znakům uloženým v přidruženém řetězci jako řetězec ve stylu C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku na data řetězce.

### <a name="remarks"></a>Poznámky

Volání této funkce vrátit ukazatel do vyrovnávací paměti znaků objektu řetězce. Obsah objektu řetězce nelze změnit pomocí tohoto ukazatele.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::operátor PXSTR

Přímo přistupuje k znakům uloženým v přidruženém řetězci jako řetězec ve stylu C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku na data řetězce.

### <a name="remarks"></a>Poznámky

Volání této funkce vrátit ukazatel do vyrovnávací paměti znaků objektu řetězce. Vývojář může změnit obsah objektu řetězce pomocí tohoto ukazatele.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR

Ukazatel na konstantní řetězec.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR

Ukazatel na řetězec.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT::SET_LENGTH

Nastavte délku objektu `GetBuffer` řetězce v čase.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Poznámky

Nastavte délku objektu řetězce v době GetBuffer.

Určuje, zda jsou při vytváření objektu vyrovnávací paměti řetězce volány [csimplestringt::GetBufferAAa](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [CSimpleStringT::GetBufferSetLength.](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::SetLength

Nastaví délku vyrovnávací paměti znaků.

```
void SetLength(int nLength);
```

### <a name="parameters"></a>Parametry

*nDélka*<br/>
Nová délka vyrovnávací paměti znaků objektu řetězce.

> [!NOTE]
> Musí být menší nebo rovna minimální délce vyrovnávací `CStrBufT`paměti určené v konstruktoru .

### <a name="remarks"></a>Poznámky

Volání této funkce nastavit délku řetězce reprezentované ho objektu vyrovnávací paměti.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::Typ řetězce

Typ řetězce, jehož vyrovnávací paměť má být manipulováno specializace této šablony třídy.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Poznámky

`TCharType`je typ znaku používaný ke specialitě šablony třídy.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
