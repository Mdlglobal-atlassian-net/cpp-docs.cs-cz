---
title: Cstrbuft – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcf0675b81d684fdf8b78e865bf754d45ef4888c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752681"
---
# <a name="cstrbuft-class"></a>Cstrbuft – třída

Tato třída poskytuje vyčištění automatické prostředků pro `GetBuffer` a `ReleaseBuffer` zavolá u existujícího `CStringT` objektu.

## <a name="syntax"></a>Syntaxe

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parametry

*TCharType*  
Znakový typ `CStrBufT` třídy. Může být jedna z následujících akcí:

- **Char** (pro řetězce znaků ANSI)

- **wchar_t** (pro řetězce znaků Unicode)

- Tchar – (pro řetězce znaků ANSI a Unicode)

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|PCXSTR|Ukazatel na konstanty typu řetězec.|
|PXSTR|Ukazatel na řetězec.|
|`StringType`|Typ řetězec, jehož vyrovnávací paměť je manipulovat specializace této třídy šablony.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Konstruktor pro objekt vyrovnávací paměti řetězce.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Nastaví délku objektu příslušný řetězcový znak vyrovnávací paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Načte **const** ukazatel do vyrovnávací paměti pro znaky přidruženými řetězcovými objektu.|
|[CStrBufT::operator PXSTR](#operator_pxstr)|Načte ukazatel do vyrovnávací paměti pro znaky přidruženými řetězcovými objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Automaticky určete nový délku řetězce při vydání verze.|
|[CStrBufT::SET_LENGTH](#set_length)|Nastavení délky na objekt řetězce v době getbuffer –|

## <a name="remarks"></a>Poznámky

Tato třída se používá jako obálkovou třídu pro nahrazení volání [getbuffer –](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), nebo [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) a `ReleaseBuffer`.

Primárně určený jako pomocnou třídu, `CStrBufT` představuje pohodlný způsob pro vývojáře pro práci s vyrovnávací paměti pro znaky z objektu typu string, ale nemusíme se starat o tom, nebo kdy se má volat `ReleaseBuffer`. Je to možné proto Obálkový objekt dostane mimo rozsah přirozeně v případě výjimku nebo více cest stávající kód; způsobuje, že jeho destruktor uvolnit prostředek řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

##  <a name="auto_length"></a>  CStrBufT::AUTO_LENGTH

Automaticky určete nový délku řetězce při vydání verze.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Poznámky

Automaticky určete nový délku řetězce při vydání verze. Musí být řetězec zakončený hodnotou null.

##  <a name="cstrbuft"></a>  CStrBufT::CStrBufT

Vytvoří objekt vyrovnávací paměti.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parametry

*str*  
Objekt řetězec přidružený k vyrovnávací paměti. Vývojář se obvykle používají předdefinované funkce typedefs z `CStrBuf` (Tchar – typ variant), `CStrBufA` (**char** typ variant) a `CStrBufW` (**wchar_t** variantu).

*nMinLength*  
Minimální délka vyrovnávací paměti pro znaky.

*dwFlags*  
Určuje, pokud je automaticky určena délka řetězce. Může být jedna z následujících akcí:

- Délka řetězce AUTO_LENGTH je automaticky určit, kdy [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) je volána. Musí být řetězec zakončený hodnotou null. Výchozí hodnota.

- Délka řetězce SET_LENGTH je nastavena, když [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) je volána.

### <a name="remarks"></a>Poznámky

Vytvoří řetězec vyrovnávací paměť pro objekt přidruženými řetězcovými. Během vytváření [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) nebo [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) je volána.

Všimněte si, že je kopírovací konstruktor **privátní**.

##  <a name="operator_pcxstr"></a>  CStrBufT::operator PCXSTR

Přímý přístup k znaků uložených v přidruženými řetězcovými objektu jako řetězec stylu C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku řetězec data.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrátí ukazatel do vyrovnávací paměti pro znaky z objektu typu string. Pomocí tohoto ukazatele nelze změnit obsah na objekt řetězce.

##  <a name="operator_pxstr"></a>  CStrBufT::operator PXSTR

Přímý přístup k znaků uložených v přidruženými řetězcovými objektu jako řetězec stylu C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku řetězec data.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrátí ukazatel do vyrovnávací paměti pro znaky z objektu typu string. Vývojář může změnit obsah na objekt řetězce s ukazatele this.

##  <a name="pcxstr"></a>  CStrBufT::PCXSTR

Ukazatel na konstanty typu řetězec.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

##  <a name="pxstr"></a>  CStrBufT::PXSTR

Ukazatel na řetězec.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

##  <a name="set_length"></a>  CStrBufT::SET_LENGTH

Nastavení délky na objekt řetězce na `GetBuffer` čas.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Poznámky

V době getbuffer – nastavte délku objektu typu string.

Určuje, zda [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) jsou volány při vytvoření objektu vyrovnávací paměti řetězce.

##  <a name="setlength"></a>  CStrBufT::SetLength

Nastaví délku vyrovnávací paměti pro znaky.

```
void SetLength(int nLength);
```

### <a name="parameters"></a>Parametry

*nLength*  
Novou velikost vyrovnávací paměti pro znaky z objektu string.

> [!NOTE]
>  Musí být menší nebo rovna minimální vyrovnávací paměti délka zadaná v konstruktoru `CStrBufT`.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavit délku řetězce reprezentovaný objektem vyrovnávací paměti.

##  <a name="stringtype"></a>  CStrBufT::StringType

Typ řetězec, jehož vyrovnávací paměť je manipulovat specializace této třídy šablony.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Poznámky

`TCharType` slouží k specializovat šablonu třídy tyto typy znaků.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)   
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

