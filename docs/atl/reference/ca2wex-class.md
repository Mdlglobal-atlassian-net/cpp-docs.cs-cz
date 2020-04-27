---
title: CA2WEX – třída
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: a710034c5d94a8fb093a2b6a2a52373e2bab2d6d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168498"
---
# <a name="ca2wex-class"></a>CA2WEX – třída

Tato třída se používá v makrech převodu řetězce CA2TEX, CA2CTEX, CT2WEX a CT2CWEX a v CA2W typedef.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <int t_nBufferLength = 128>
class CA2WEX
```

### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Konstruktor|
|[CA2WEX:: ~ CA2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CA2WEX:: operator LPWSTR](#operator_lpwstr)|Operátor převodu|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CA2WEX:: m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CA2WEX:: m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud nejsou potřeba žádné další funkce, použijte ve svém kódu CA2TEX, CA2CTEX, CT2WEX, CT2CWEX nebo CA2W.

Tato třída obsahuje statickou vyrovnávací paměť pevné velikosti, která se používá k uložení výsledku převodu. Je-li výsledek příliš velký, aby se vešel do statické vyrovnávací paměti, třída přiděluje paměť **pomocí třídy**typu \ a uvolní paměť, když se objekt dostane mimo rozsah. Tím je zajištěno, že na rozdíl od maker převodu textu dostupných v předchozích verzích knihovny ATL je tato třída bezpečná pro použití ve smyčkách a její přetečení do zásobníku.

Pokud se třída pokusí přidělit paměť na haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají převodní třídy a makra knihovny ATL k převodu znakovou stránku ANSI aktuálního vlákna. Pokud chcete toto chování přepsat pro určitý převod, zadejte znakovou stránku jako druhý parametr do konstruktoru třídy.

Následující makra jsou založena na této třídě:

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

Následující definice typedef je založena na této třídě:

- CA2W

Diskuzi o těchto makrech převodu textu viz [makra ATL a MFC String Conversion](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto maker převodů řetězců naleznete v tématech [ATL a makra převodu řetězců knihovny MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv. h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

Konstruktor

```cpp
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Znaková stránka, která se používá k provedení převodu Další podrobnosti najdete v tématu diskuze parametru kódové stránky pro Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) funkce.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměť použitou v procesu překladu.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX:: ~ CA2WEX

Destruktor.

```cpp
~CA2WEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX:: m_psz

Datový člen, který ukládá zdrojový řetězec.

```cpp
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX:: m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```cpp
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX:: operator LPWSTR

Operátor převodu

```cpp
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPWSTR.

## <a name="see-also"></a>Viz také

[CA2AEX – třída](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX – třída](../../atl/reference/ca2caex-class.md)<br/>
[CW2AEX – třída](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX – třída](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
