# 📊 Storage Array Inventory & Health Report

**Generated:** November 23, 2025  
**Location:** Homelab Storage Array Documentation

---

## 🎯 Executive Summary Dashboard

| Drive | Localização | Modelo | Capacidade | Saúde | Uso (Tempo) | Status Visual |
|-------|-----------|--------|-----------|-------|------------|----------------|
| **C: / G:** | Desktop | Samsung 980 PRO 1TB | 953 GB | 🟢 IMPECÁVEL | 1.5 anos | ⚡ Alto Desempenho |
| **D:** | Desktop | Seagate Ironwolf 4TB | 3.8 TB | 🟢 IMPECÁVEL | 6.6 meses | 💾 NAS Grade |
| **H:** | Homelab | Seagate Exos X24 24TB | 24.0 TB | 🟢 IMPECÁVEL (Enterprise) | 61h (novo) | 🏆 Enterprise Grade |
| **M:** | External | Seagate Momentus 750GB | 715 GB | 🟡 RISCO | 1.15 anos | ⚠️ Alto risco de dados |
| **P:** | External | Seagate Expansion 2TB | 1.9 TB | 🟢 IMPECÁVEL (Físico) | 2.9 anos | 📸 Backup Fotos |
| **R:** | Desktop | Seagate Ironwolf 4TB | 3.8 TB | 🟢 IMPECÁVEL | ~3.8 anos | 🎮 Retrogaming |
| **S:** | External | Seagate Expansion 12TB | 11.4 TB | 🟢 IMPECÁVEL | 5.5 meses | 📺 Media Server |
| **V:** | External | Seagate Momentus 700GB | 715 GB | 🟢 ÓTIMA | 9.4 meses | 💨 Vazio/Backup |
| **Z:** | Desktop | Seagate Barracuda 4TB | 3.8 TB | 🔴 ALTO RISCO | 4.36 anos | ☠️ Zombie Drive |

---

## 📈 Resumo de Saúde Geral

- **✅ Drives Saudáveis:** 7/9 (78%)
- **⚠️ Drives em Risco:** 1/9 (11%)
- **🔴 Drives Críticos:** 1/9 (11%)
- **💾 Capacidade Total:** ~64.9 TB
- **📊 Recomendação Imediata:** Retire o drive Z: de operação e considere migrar dados do M:

---

## 🔍 Análise Detalhada por Unidade

---

### ## Drive C: / G: - Samsung 980 PRO [Gaming]

![Imagem do Drive C](./storages/C%20G%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Samsung |
| **Modelo** | SSD 980 PRO 1TB |
| **Número de Série** | S5P2NG0R933687D |
| **Interface** | PCI-Express 4.0 x4 (NVMe) |
| **Firmware** | 3B2QGXA7 |
| **Capacidade Real** | 953 GB |
| **Formato Físico** | M.2 2280 |
| **Tipo de Memória** | Samsung 128-layer 3D TLC V-NAND |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **IMPECÁVEL**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 13.676 horas (~1.5 anos) | ✅ |
| **Ciclos de Potência** | 1.832 | ✅ |
| **Desligamentos Não Seguros** | 59 | ⚠️ Moderado |
| **Temperatura Máxima** | 64°C | ✅ (Limiar: 82°C) |
| **Vida Útil Restante** | 79% (Available Spare: 100%) | ✅ Excelente |
| **Uso do Ciclo de Vida** | 21% | ✅ |
| **Erros de Integridade** | 0 | ✅ Nenhum |
| **Critical Warning** | 0 | ✅ Nenhum |

**Observações:**
> Este é um SSD de alto desempenho (PCIe 4.0), operando com níveis de uso e temperatura totalmente saudáveis. O drive ainda tem 79% da sua vida útil. Ideal para gaming e aplicações exigentes.

---

### ## Drive D: - Ironwolf [Dados]

![Imagem do Drive D](./storages/D%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Ironwolf ST4000VN006-3CW104 |
| **Número de Série** | ZW62M4K7 |
| **Interface** | SATA III (6 Gbps) |
| **Firmware** | SC60 |
| **Capacidade Real** | 3.8 TB (3.815 TB) |
| **RPM** | 5400 RPM |
| **Formato Físico** | 3.5" Fixed Disk |
| **Data de Instalação** | 16/08/2025 |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **IMPECÁVEL**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 4.760 horas (~6.6 meses) | ✅ Novo |
| **Ciclos de Potência** | 569 | ✅ |
| **Setores Realocados** | 0 | ✅ Nenhum |
| **Setores Pendentes** | 0 | ✅ Nenhum |
| **Erros Não Corrigíveis** | 0 | ✅ Nenhum |
| **Temperatura de Ar** | 42°C | ✅ |
| **Teste Self-Test** | ✅ Sucesso (11/23/2025) | ✅ |
| **Todos Atributos SMART** | OK | ✅ Zero falhas |

**Observações:**
> Este é um drive **Seagate Ironwolf**, modelo NAS/Dados, em condição perfeita (zero falhas SMART). O drive está em um estágio inicial de uso e é totalmente confiável para armazenar dados primários, como fotos e documentos.

---

### ## Drive H: - Seagate Exos X24 [Homelab]

![Imagem do Drive H](./storages/H%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Exos X24 (Enterprise Grade) |
| **Número de Série** | ZYD0CB2X |
| **Interface** | SATA III (6 Gbps) |
| **Firmware** | SN04 |
| **Capacidade Real** | 24.0 TB |
| **RPM** | 7200 RPM |
| **Formato Físico** | 3.5" Fixed Disk |
| **Setores** | 512B (lógico) / 4096B (físico) |
| **Classe** | Enterprise-Grade NAS/Surveillance |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **IMPECÁVEL (Enterprise Grade)**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 61 horas (praticamente novo) | ✅ Novo |
| **Ciclos de Potência** | 5 | ✅ |
| **Setores Realocados** | 0 | ✅ Nenhum |
| **Setores Pendentes** | 0 | ✅ Nenhum |
| **Temperatura** | 43°C | ✅ |
| **Ciclos de Carga** | 8 | ✅ |
| **SMART Status** | ✅ Todas OK | ✅ |

**Observações:**
> Drive Seagate Exos X24 (24TB), Enterprise Grade, em estado de novo. Perfeito para a função de Homelab e Media Server. É o drive mais confiável e performático do seu setup, com design otimizado para 24/7 operation.

---

### ## Drive M: - Seagate Momentus [Music Backup]

![Imagem do Drive M](./storages/M%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Momentus 7200.5 (ST9750420AS) |
| **Número de Série** | 5WS3JQCF |
| **Interface** | USB 3.0 UASP / SATA II |
| **Firmware** | 0003HPM1 |
| **Capacidade Real** | 715 GB |
| **RPM** | 7200 RPM |
| **Formato Físico** | 2.5" Fixed Disk (Portátil) |
| **Controlador USB** | ASMT1051 |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟡 **INSTÁVEL / ALTO RISCO DE DADOS**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 10.053 horas (~1.15 anos) | ⚠️ |
| **Ciclos de Potência** | 2.036 | ⚠️ Alto |
| **Setores Realocados** | 0 | ✅ |
| **Setores Pendentes** | **171** | 🔴 CRÍTICO |
| **Erros Não Corrigíveis** | **939** | 🔴 CRÍTICO |
| **G-Sense Error Rate** | **1057** | 🔴 Impactos físicos detectados |

**Observações:**
> ⚠️ **ALERTA:** O drive está fisicamente bem (0 realocações), mas o **alto número de setores pendentes (171) e erros não corrigíveis (939)** indica **instabilidade de leitura e risco significativo de perda de dados**. A taxa de erros G-Sense (1057) sugere que o drive sofreu impactos físicos.
>
> **Recomendação:** Não use como único backup. Migre dados críticos para outro drive imediatamente. Use-o no máximo para dados que podem ser rebaixados ou redundantes.

---

### ## Drive P: - Seagate Expansion [Photos]

![Imagem do Drive P](./storages/P%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Expansion Desk (ST2000VN004-2E4164) |
| **Número de Série** | Z520600H |
| **Interface** | USB 3.0 UASP / SATA III |
| **Firmware** | SC60 |
| **Capacidade Real** | 1.9 TB (2TB nominal) |
| **RPM** | 5900 RPM |
| **Formato Físico** | 3.5" Fixed Disk (Enclosure externo) |
| **Buffer** | 65536 KB |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **IMPECÁVEL (Físico)**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 25.485 horas (~2.9 anos) | ✅ |
| **Ciclos de Potência** | 4.368 | ✅ |
| **Setores Realocados** | 0 | ✅ Nenhum |
| **Setores Pendentes** | 0 | ✅ Nenhum |
| **Erros Não Corrigíveis** | 0 | ✅ Nenhum |
| **Erros CRC (USB)** | **8.764** | ⚠️ Conexão USB |
| **Command Timeout** | **604** | ⚠️ Conexão USB |

**Observações:**
> 🔷 **Físico OK, Conexão Problemática:** O disco físico (IronWolf 2TB, 5900 RPM) está **perfeito e essencial para backups de fotos**. Os altos números de erros CRC (8.764) e Timeout (604) sugerem problemas na **conexão USB/cabo ou no enclosure**, não no disco em si. Isso é mitigado pela prática de mantê-lo desconectado, usando apenas para backup semestral.
>
> **Recomendação:** Teste com outro cabo USB ou enclosure para descartar problemas de conexão.

---

### ## Drive R: - Seagate Ironwolf [Retrogaming]

![Imagem do Drive R](./storages/R%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Ironwolf (ST4000VN008-2DR166) |
| **Número de Série** | ZDHBVLVQ |
| **Interface** | SATA III (6 Gbps) |
| **Firmware** | SC60 |
| **Capacidade Real** | 3.8 TB (4TB nominal) |
| **RPM** | 5900 RPM |
| **Formato Físico** | 3.5" Fixed Disk |
| **Buffer** | 65536 KB |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **IMPECÁVEL**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 13.735 horas (~3.8 anos) | ✅ Maduro |
| **Ciclos de Potência** | 5.785 | ✅ |
| **Setores Realocados** | 0 | ✅ Nenhum |
| **Setores Pendentes** | 0 | ✅ Nenhum |
| **Temperatura** | 45°C | ✅ |
| **Teste Self-Test** | ✅ OK | ✅ |
| **Todos Atributos SMART** | OK | ✅ Zero falhas |

**Observações:**
> Drive Seagate IronWolf de 4TB em excelente estado após 3.8 anos de operação. Ideal para armazenamento a longo prazo de coleções de mídia estáticas como a sua biblioteca de Retrogaming. Totalmente confiável e recomendado para manter.

---

### ## Drive S: - Seagate Expansion [Media Server Backup]

![Imagem do Drive S](./storages/S%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Expansion Desk (ST12000VN0008-2JH101) |
| **Número de Série** | ZH3MKAD4 |
| **Interface** | USB 3.0 UASP / SATA III |
| **Firmware** | DN01 |
| **Capacidade Real** | 11.4 TB (12TB nominal) |
| **RPM** | 7200 RPM |
| **Formato Físico** | 3.5" Fixed Disk (Enclosure externo) |
| **Controlador USB** | ASMT1051 |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **IMPECÁVEL**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 4.005 horas (~5.5 meses) | ✅ Novo |
| **Ciclos de Potência** | 352 | ✅ |
| **Setores Realocados** | 0 | ✅ Nenhum |
| **Setores Pendentes** | 0 | ✅ Nenhum |
| **Erros Não Corrigíveis** | 0 | ✅ Nenhum |
| **Temperatura** | 36°C | ✅ Ótima |
| **Teste Self-Test** | ✅ Sucesso (27/09/2025) | ✅ |

**Observações:**
> Drive de alta capacidade (12TB) em condição perfeita. Operando a 7200 RPM, é ideal para o backup da sua biblioteca de mídia do Homelab, oferecendo boa velocidade de acesso para um drive externo. Recomendado para manter como backup primário de mídia.

---

### ## Drive V: - Seagate Momentus [Vazio/Backup]

![Imagem do Drive V](./storages/V%20Drive.png)

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Momentus 7200.5 (ST9750422AS) |
| **Número de Série** | 6WS2KZDG |
| **Interface** | USB 3.0 UASP / SATA II |
| **Firmware** | 0001BSM1 |
| **Capacidade Real** | 715 GB |
| **RPM** | 7200 RPM |
| **Formato Físico** | 2.5" Laptop |
| **Data de Fabricação** | Junho 2012 |
| **Tempo de Procura Média** | 11.0 ms |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🟢 **ÓTIMA**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 6.815 horas (~9.4 meses) | ✅ |
| **Ciclos de Potência** | 2.569 | ✅ |
| **Setores Realocados** | 0 | ✅ Nenhum |
| **Setores Pendentes** | 0 | ✅ Nenhum |
| **Erros Não Corrigíveis** | 0 | ✅ Nenhum |
| **Ciclos de Carga/Descarrega** | 59.523 | ✅ |
| **Todos Atributos SMART** | OK | ✅ Zero falhas |

**Observações:**
> Drive SATA II de 7200 RPM (Momentus). Está em **MUITO BOA CONDIÇÃO para sua idade (2012)** com 0 falhas reportadas. A velocidade de 7200 RPM é ideal para backup ou transferência externa de dados. Pode ser usado livremente como drive de backup portátil.

---

### ## Drive Z: - Seagate Barracuda [⚠️ Zombie Drive]

![Imagem do Drive Z](./storages/Z%20Drive.png)

> ⚠️ **AVISO CRÍTICO:** Este drive está em falha progressiva e apresenta risco significativo de perda de dados. Use apenas para dados dispensáveis ou já duplicados.

#### 📋 Ficha Técnica

| Campo | Valor |
|-------|-------|
| **Fabricante** | Seagate Technology |
| **Modelo** | Barracuda 7200.12 (ST4000DM000-1F2168) |
| **Número de Série** | W301A371 |
| **Interface** | SATA III (6 Gbps) |
| **Firmware** | CC54 |
| **Capacidade Real** | 3.8 TB (4TB nominal) |
| **RPM** | 5900 RPM |
| **Formato Físico** | 3.5" Fixed Disk |
| **Buffer** | 65536 KB |

#### 🏥 Diagnóstico de Saúde

**Status Geral:** 🔴 **ALTO RISCO / FALHA PROGRESSIVA**

| Métrica | Valor | Status |
|---------|-------|--------|
| **Tempo de Vida** | 38.215 horas (~4.36 anos) | ⚠️ Envelhecido |
| **Ciclos de Potência** | 3.101 | ⚠️ |
| **Setores Realocados** | **1.208** | 🔴 CRÍTICO |
| **Setores Pendentes** | 0 | ✅ |
| **Erros Não Corrigíveis** | **2.445** | 🔴 CRÍTICO |
| **Erros CRC** | 0 | ✅ |
| **Temperatura de Ar** | 46°C | ⚠️ Moderada |
| **Teste Self-Test** | ✅ Sucesso (último) | ⚠️ |

**Observações:**
> 🔴 **EMERGÊNCIA:** Drive em falha progressiva confirmada pelo **altíssimo número de setores realocados (1.208) e erros não corrigíveis (2.445)**. O Seagate Barracuda 4TB de 5900 RPM já completou seu ciclo de vida útil.
>
> **Recomendação URGENTE:**
> 1. ⚠️ Retire este drive de operação o quanto antes
> 2. 📋 Migre dados críticos para outro drive (H:, S: ou R:)
> 3. 🗑️ Descarte ou coloque em armazenamento de emergência apenas
> 4. 🔒 Se reter, use EXCLUSIVAMENTE para dados que podem ser perdidos

---

## 📊 Matriz de Risco e Recomendações

| Drive | Risco Atual | Ação Recomendada | Urgência | Prazo |
|-------|-----------|------------------|----------|-------|
| **C: / G:** | ✅ Baixo | Manutenção normal | - | Contínuo |
| **D:** | ✅ Baixo | Manutenção normal | - | Contínuo |
| **H:** | ✅ Nenhum | Monitorar | - | Contínuo |
| **M:** | 🟡 Médio-Alto | Migrar dados imediatamente | 🔴 ALTA | 1-2 semanas |
| **P:** | ✅ Baixo (Físico) | Testar cabo USB | - | ASAP |
| **R:** | ✅ Baixo | Manutenção normal | - | Contínuo |
| **S:** | ✅ Baixo | Manutenção normal | - | Contínuo |
| **V:** | ✅ Baixo | Manutenção normal | - | Contínuo |
| **Z:** | 🔴 CRÍTICO | ⚠️ **REMOVER DE OPERAÇÃO** | 🔴 CRÍTICA | **IMEDIATO** |

---

## 🔧 Plano de Ação Recomendado

### Ações Imediatas (Hoje - 1 semana)

1. **Z: (Zombie Drive)**
   - ❌ Parar de usar imediatamente
   - 📋 Migrar dados para H:, S: ou R:
   - 🗑️ Descartar ou armazenar offline

2. **M: (Music Backup)**
   - ⚠️ Testar e fazer backup de dados críticos
   - 📋 Migrar para novo drive se houver dados importantes
   - 🔍 Monitorar próximas 2 semanas antes de decisão final

3. **P: (Photos)**
   - 🧪 Testar com outro cabo USB 3.0
   - 🔧 Se problema persistir, considerar novo enclosure

### Ações a Médio Prazo (1-3 meses)

1. **Implementar Backup 3-2-1**
   - 3 cópias de dados críticos
   - 2 tipos diferentes de mídia
   - 1 offsite (nuvem ou local seguro)

2. **Monitorar H: regularmente**
   - Verificar SMART mensalmente
   - Este é seu drive mais confiável - mantenha backups

3. **Considerar SSD adicional**
   - C: está em 21% de ciclo de vida
   - Futuramente, considerar upgrade para 2TB quando necessário

### Ações a Longo Prazo (6-12 meses)

1. **Planejar substituição**
   - V: (Momentus 700GB) - considerar aposentar
   - P: (Expansion 2TB) - avaliar depois de 3-4 anos
   - R: (Ironwolf 4TB) - está em bom estado, pode manter +1-2 anos

2. **Upgrade de Capacidade**
   - Considerar adicionar mais storage Exos X24 se expandir necessidade

---

## 📈 Estatísticas Gerais

### Capacidade

| Tipo | Quantidade | Capacidade | Percentual |
|------|-----------|-----------|-----------|
| **SSD** | 1 | 953 GB | 1.5% |
| **HDD Interno** | 3 | 11.4 TB | 17.5% |
| **HDD Externo** | 5 | 52.5 TB | 81% |
| **TOTAL** | 9 | **64.9 TB** | 100% |

### Saúde

| Status | Quantidade | Drives |
|--------|-----------|--------|
| 🟢 Impecável | 7 | C/G, D, H, P, R, S, V |
| 🟡 Risco | 1 | M |
| 🔴 Crítico | 1 | Z |

### Idade

| Classificação | Quantidade | Exemplos |
|---------------|-----------|----------|
| Novo (<1 ano) | 3 | C/G (1.5 anos), H (novo), S (5.5 meses) |
| Maduro (1-3 anos) | 3 | D (6.6 meses), M (1.15 anos), V (9.4 meses) |
| Envelhecido (>3 anos) | 3 | P (2.9 anos), R (3.8 anos), Z (4.36 anos) |

---

## 🔐 Checklist de Segurança de Dados

- [ ] Backup de dados críticos no drive H: (Exos 24TB)
- [ ] Backup de fotos em P: testado e verificado
- [ ] S: testado para backup de mídia
- [ ] Plano 3-2-1 implementado
- [ ] Z: removido de operação
- [ ] M: migrado ou descartado
- [ ] Monitoramento SMART mensal ativado
- [ ] Teste de restore realizado nos últimos 3 meses

---

**Documento gerado:** 23 de Novembro de 2025  
**Próxima revisão recomendada:** 23 de Dezembro de 2025  
**Proprietário:** mfrafael  
**Nível de Confidencialidade:** Documentação Técnica
