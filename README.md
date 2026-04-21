def process_daily_deduction(driver_balance):
    POTONGAN_FIXED = 270000
    ALOKASI_CICILAN = 240000
    ALOKASI_MAINTENANCE = 30000
    
    if driver_balance >= POTONGAN_FIXED:
        driver_balance -= POTONGAN_FIXED
        payment_status = "LUNAS"
        to_cicilan = ALOKASI_CICILAN
        to_maintenance = ALOKASI_MAINTENANCE
    else:
        # Jika saldo kurang, sistem menandai hutang
        payment_status = "TUNGGAKAN"
        to_cicilan = 0
        to_maintenance = 0
        
    return {
        "status_pembayaran": payment_status,
        "sisa_saldo_driver": driver_balance,
        "masuk_tabungan_servis": to_maintenance
    }

# Simulasi Driver dengan saldo 500rb
print(process_daily_deduction(500000))
