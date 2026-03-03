# Fabrication Checklist — Mutebox HAT

## 1. Schematic
- [ ] Run ERC (Electrical Rules Check) — zero errors
- [ ] All power pins connected
- [ ] No dangling wire stubs (check for arrow markers)
- [ ] DNP set correctly on ghost/suppressed components
- [ ] LCSC Part Number populated for all assembled parts
- [ ] No duplicate LCSC numbers across different value parts
- [ ] Component values consistent (e.g. no "10K" vs "10k" mismatches)

## 2. PCB
- [ ] Run DRC — zero errors, zero unconnected items
- [ ] Verify ratsnest is empty (no airwires remaining)
- [ ] Check board edge/courtyard clearances
- [ ] Confirm component orientations (especially ICs, polarized caps, LEDs)
- [ ] Run DRC **again after any last-minute edits**

## 3. Export BOM
- [ ] Group symbols enabled
- [ ] Exclude DNP checked
- [ ] All real parts have LCSC numbers
- [ ] No duplicate LCSC numbers across different parts
- [ ] Paste into Claude for format check → output `bom_jlcpcb.csv`

## 4. Export CPL
- [ ] File → Fabrication Outputs → Component Placement
- [ ] Top side only (unless you have bottom components)
- [ ] Paste into Claude for format check → output `cpl_jlcpcb.csv`

## 5. Export Gerbers
- [ ] All copper layers
- [ ] F.Mask, B.Mask
- [ ] F.Silkscreen
- [ ] Edge.Cuts
- [ ] Drill file (excellon)
- [ ] Zip and verify in Gerber viewer before upload

## 6. Claude Format Pass
Paste BOM and CPL and confirm:
- [ ] BOM headers: `Comment, Designator, Footprint, LCSC Part Number`
- [ ] CPL headers: `Designator, Val, Package, Mid X, Mid Y, Rotation, Layer`
- [ ] No quoted values in CPL
- [ ] No library prefixes in Footprint column
- [ ] No duplicate or comma-separated LCSC numbers

## 7. JLCPCB Upload
- [ ] Gerbers accepted, board outline looks correct
- [ ] BOM uploaded, all parts matched
- [ ] CPL uploaded, placements look correct in preview
- [ ] Check component rotation preview for ICs
- [ ] Confirm order details and quantities

## 8. Git
- [ ] Commit schematic, PCB, and fabrication files
- [ ] Tag release: `git tag vX.X && git push origin vX.X`
