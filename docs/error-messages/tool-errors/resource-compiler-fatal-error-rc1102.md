---
title: Závažná chyba kompilátoru prostředků RC1102
ms.date: 11/04/2016
f1_keywords:
- RC1102
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
ms.openlocfilehash: e614a7e85f508a452f42588fe40054dfcc8a7089
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182477"
---
# <a name="resource-compiler-fatal-error-rc1102"></a>Závažná chyba kompilátoru prostředků RC1102

Vnitřní chyba: příliš mnoho argumentů pro RCPP

Preprocesoru kompilátoru prostředků bylo předáno příliš mnoho argumentů. Snižte počet symbolů definovaných pomocí možnosti definovat symboly (/d) jejich definováním ve zdroji. Tato chyba může být také způsobena tím, že zadáte příliš mnoho cest hledání souborů include pomocí možnosti cesty hledání include (/i).
