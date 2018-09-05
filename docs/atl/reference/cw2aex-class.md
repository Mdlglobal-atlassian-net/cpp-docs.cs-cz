---
title: Cw2aex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cd88555ee28b7bdddef51371ba2774047464678
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759480"
---
# <a name="cw2aex-class"></a>Cw2aex – třída

Tato třída se používá makra převodu řetězců CT2AEX, CW2TEX, CW2CTEX a CT2CAEX a definice typedef CW2A.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>  
class CW2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*  
Velikost vyrovnávací paměti používané při překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Konstruktor|
|[CW2AEX –:: ~ CW2AEX –](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CW2AEX::Operator LPSTR](#operator_lpstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte CT2AEX, CW2TEX, CW2CTEX, CT2CAEX nebo CW2A ve vašem kódu.

Tato třída obsahuje pevné velikosti vyrovnávací paměti statické, která slouží k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde do statické vyrovnávací paměti, třída přiděluje paměť pomocí **malloc**, uvolnění paměti, když objekt dostane mimo rozsah. To zajišťuje, že na rozdíl od text makra převodů, které jsou k dispozici v předchozích verzích knihovny ATL, tato třída je bezpečné používat ve smyčkách a že nebudou přetečení zásobníku.

Pokud třída pokusí o přidělení paměti v haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají převodu třídy ATL a makra znakovou stránku ANSI aktuální vlákno pro převod. Pokud chcete přepsat toto chování pro konkrétní převod, zadejte jako druhý parametr konstruktoru pro třídu znakovou stránku.

Následující makra jsou založené na této třídě:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Následující definice typedef je založena na této třídě:

- CW2A

Informace o těchto makrech převodu textu, naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md).

## <a name="example"></a>Příklad

Zobrazit [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

##  <a name="cw2aex"></a>  CW2AEX::CW2AEX

Konstruktor

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*  
Textový řetězec, který má být převeden.

*nCodePage*  
Znaková stránka používá k provedení převodu. Viz diskuze parametr stránky kód pro funkci Windows SDK [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar) další podrobnosti.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměti používané při překladu.

##  <a name="dtor"></a>  CW2AEX –:: ~ CW2AEX –

Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělené vyrovnávací paměti.

##  <a name="m_psz"></a>  CW2AEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

Statické vyrovnávací paměť, používá k ukládání převedený řetězec.

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CW2AEX::Operator LPSTR

Operátor převodu.

```  
operator LPSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typu LPSTR.

## <a name="see-also"></a>Viz také

[Ca2aex – třída](../../atl/reference/ca2aex-class.md)   
[Ca2caex – třída](../../atl/reference/ca2caex-class.md)   
[Ca2wex – třída](../../atl/reference/ca2wex-class.md)   
[Cw2cwex – třída](../../atl/reference/cw2cwex-class.md)   
[Cw2wex – třída](../../atl/reference/cw2wex-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
