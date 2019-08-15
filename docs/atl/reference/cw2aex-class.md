---
title: CW2AEX – třída
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 4dda1cb9e54c44f7940475660bc629192b9ead61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496270"
---
# <a name="cw2aex-class"></a>CW2AEX – třída

Tato třída se používá v makrech převodu řetězce CT2AEX, CW2TEX, CW2CTEX a CT2CAEX a v CW2A typedef.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Konstruktor|
|[CW2AEX::~CW2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CW2AEX:: operator typem LPStr](#operator_lpstr)|Operátor převodu|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud nejsou potřeba žádné další funkce, použijte ve svém kódu CT2AEX, CW2TEX, CW2CTEX, CT2CAEX nebo CW2A.

Tato třída obsahuje statickou vyrovnávací paměť pevné velikosti, která se používá k uložení výsledku převodu. Je-li výsledek příliš velký, aby se vešel do statické vyrovnávací paměti, třída přiděluje paměťpomocí třídy typu \ a uvolní paměť, když se objekt dostane mimo rozsah. Tím je zajištěno, že na rozdíl od maker převodu textu dostupných v předchozích verzích knihovny ATL je tato třída bezpečná pro použití ve smyčkách a její přetečení do zásobníku.

Pokud se třída pokusí o přidělení paměti v haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají převodní třídy a makra knihovny ATL k převodu znakovou stránku ANSI aktuálního vlákna. Pokud chcete toto chování přepsat pro určitý převod, zadejte znakovou stránku jako druhý parametr do konstruktoru třídy.

Následující makra jsou založena na této třídě:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Následující definice typedef je založena na této třídě:

- CW2A

Diskuzi o těchto makrech převodu textu viz [makra ATL a MFC String Conversion](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto maker převodů řetězců naleznete v tématech [ATL a makra převodu řetězců knihovny MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv. h

##  <a name="cw2aex"></a>CW2AEX::CW2AEX

Konstruktor

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Znaková stránka, která se používá k provedení převodu Další podrobnosti najdete v tématu diskuze parametru kódové stránky pro Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) funkce.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměť použitou v procesu překladu.

##  <a name="dtor"></a>  CW2AEX::~CW2AEX

Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

##  <a name="m_psz"></a>  CW2AEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>CW2AEX:: operator typem LPStr

Operátor převodu

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ typem LPStr.

## <a name="see-also"></a>Viz také:

[CA2AEX – třída](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX – třída](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX – třída](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX – třída](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
