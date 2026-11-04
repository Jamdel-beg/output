import React, { useState, useEffect, useMemo } from 'react';
import { 
  LayoutDashboard, 
  CheckSquare, 
  Wallet, 
  CreditCard, 
  BarChart3, 
  Calendar as CalendarIcon, 
  Download, 
  RotateCcw, 
  Plus, 
  Search, 
  CheckCircle2, 
  Clock, 
  DollarSign, 
  ChevronRight, 
  ShieldCheck, 
  Building2, 
  FileSpreadsheet, 
  Info,
  Save
} from 'lucide-react';

// --- INITIAL DEBT SCHEDULE DATA (IMPORTED FROM SOURCE SHEET) ---
const INITIAL_LOANS = [
  { id: 'loan-1', name: 'TikTok', monthlyAmount: 1878, originalPrincipal: 3756, dueDate: 18, totalMonths: 2, payoffDate: '2027-01-18', splits: 2, icon: 'ShoppingBag' },
  { id: 'loan-2', name: 'Shopee', monthlyAmount: 788.04, originalPrincipal: 7092.36, dueDate: 11, totalMonths: 9, payoffDate: '2027-07-11', splits: 2, icon: 'ShoppingBag' },
  { id: 'loan-3', name: 'HC Qwarta', monthlyAmount: 1500, originalPrincipal: 24000, dueDate: 24, totalMonths: 16, payoffDate: '2028-02-24', splits: 2, icon: 'CreditCard' },
  { id: 'loan-4', name: 'HC 150K', monthlyAmount: 7519, originalPrincipal: 195494, dueDate: 6, totalMonths: 26, payoffDate: '2029-01-06', splits: 1, icon: 'Landmark' },
  { id: 'loan-5', name: 'HC 20K', monthlyAmount: 1558, originalPrincipal: 15580, dueDate: 28, totalMonths: 10, payoffDate: '2027-08-28', splits: 2, icon: 'CreditCard' },
  { id: 'loan-6', name: 'GCash', monthlyAmount: 571.17, originalPrincipal: 3998.19, dueDate: 30, totalMonths: 7, payoffDate: '2027-05-30', splits: 1, icon: 'Smartphone' },
  { id: 'loan-7', name: 'Maya CC', monthlyAmount: 3000, originalPrincipal: 54000, dueDate: 13, totalMonths: 18, payoffDate: '2028-05-13', splits: 1, icon: 'CreditCard' },
  { id: 'loan-8', name: 'Atome Cash', monthlyAmount: 5355, originalPrincipal: 48195, dueDate: 15, totalMonths: 9, payoffDate: '2027-08-15', splits: 1, startMonth: '2027-02', icon: 'Coins' },
  { id: 'loan-9', name: 'Uno Bank', monthlyAmount: 4100, originalPrincipal: 20500, dueDate: 1, totalMonths: 5, payoffDate: '2027-04-01', splits: 1, icon: 'Building2' },
  { id: 'loan-10', name: 'BDO CC', monthlyAmount: 1000, originalPrincipal: 18000, dueDate: 14, totalMonths: 18, payoffDate: '2028-05-14', splits: 1, icon: 'CreditCard' },
  { id: 'loan-11', name: 'Car', monthlyAmount: 7250, originalPrincipal: 174000, dueDate: 18, totalMonths: 24, payoffDate: '2028-10-18', splits: 2, icon: 'Car' }
];

// Alphanumeric date helper (e.g., "Nov 18, 2026")
const formatAlphaDate = (dateStr) => {
  if (!dateStr) return '-';
  const parts = dateStr.split('-');
  if (parts.length !== 3) return dateStr;
  const [year, month, day] = parts;
  const dateObj = new Date(parseInt(year), parseInt(month) - 1, parseInt(day));
  if (isNaN(dateObj.getTime())) return dateStr;
  return dateObj.toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' });
};

// Generate standard salary periods list (Nov 2026 - Dec 2028)
const generateSalaryPeriods = () => {
  const periods = [];
  const startYear = 2026;
  const endYear = 2028;

  for (let year = startYear; year <= endYear; year++) {
    const startMonth = year === 2026 ? 11 : 1; // Start Nov 2026
    for (let month = startMonth; month <= 12; month++) {
      const monthName = new Date(year, month - 1, 1).toLocaleString('default', { month: 'long' });
      const mStr = month < 10 ? `0${month}` : `${month}`;
      
      periods.push({
        id: `${year}-${mStr}-P1`,
        name: `${monthName} 1–15, ${year}`,
        year,
        month,
        half: 1,
        salary: 25000
      });

      periods.push({
        id: `${year}-${mStr}-P2`,
        name: `${monthName} 16–${new Date(year, month, 0).getDate()}, ${year}`,
        year,
        month,
        half: 2,
        salary: 25000
      });
    }
  }
  return periods;
};

// Seed schedule payments based on excel source rules
const generateInitialPayments = (periods) => {
  const payments = [];
  let idCounter = 1;

  periods.forEach((period) => {
    const { year, month, half, id: periodId, name: periodName } = period;

    const addP = (loanName, instNum, actualDueDateStr, amount, remarks = '') => {
      payments.push({
        id: `pmt-${idCounter++}`,
        loanName,
        installmentNumber: instNum,
        periodId,
        periodName,
        dueDate: actualDueDateStr,
        amount,
        status: 'PENDING',
        paidDate: null,
        remarks: remarks || `Scheduled allocation for ${periodName}`
      });
    };

    const monthStr = month < 10 ? `0${month}` : `${month}`;
    const nextMonth = month === 12 ? 1 : month + 1;
    const nextYear = month === 12 ? year + 1 : year;
    const nextMonthStr = nextMonth < 10 ? `0${nextMonth}` : `${nextMonth}`;

    // 1. TikTok (2 mos: Nov 2026 - Dec 2026)
    if (year === 2026 && (month === 11 || month === 12)) {
      if (half === 1) addP('TikTok', 2, `${year}-${monthStr}-18`, 1878.00);
      else addP('TikTok', 1, `${nextYear}-${nextMonthStr}-18`, 939.00);
    }

    // 2. Shopee (9 mos: Nov 2026 - Jul 2027)
    if ((year === 2026 && month >= 11) || (year === 2027 && month <= 7)) {
      if (half === 1) addP('Shopee', 2, `${year}-${monthStr}-11`, 788.04);
      else addP('Shopee', 1, `${nextYear}-${nextMonthStr}-11`, 394.02);
    }

    // 3. HC Qwarta (16 mos: Nov 2026 - Feb 2028)
    if ((year === 2026 && month >= 11) || year === 2027 || (year === 2028 && month <= 2)) {
      if (half === 1) addP('HC Qwarta', 2, `${year}-${monthStr}-24`, 1500.00);
      else addP('HC Qwarta', 1, `${nextYear}-${nextMonthStr}-24`, 750.00);
    }

    // 4. HC 150K (26 mos: Nov 2026 - Dec 2028)
    if (year >= 2026 && year <= 2028) {
      if (!(year === 2026 && month < 11)) {
        if (half === 1) addP('HC 150K', 1, `${nextYear}-${nextMonthStr}-06`, 3759.50);
        else addP('HC 150K', 2, `${nextYear}-${nextMonthStr}-06`, 3759.50);
      }
    }

    // 5. HC 20K (10 mos: Nov 2026 - Aug 2027)
    if ((year === 2026 && month >= 11) || (year === 2027 && month <= 8)) {
      if (half === 1) addP('HC 20K', 2, `${year}-${monthStr}-28`, 1558.00);
      else addP('HC 20K', 1, `${nextYear}-${nextMonthStr}-28`, 779.00);
    }

    // 6. GCash (7 mos: Nov 2026 - May 2027)
    if ((year === 2026 && month >= 11) || (year === 2027 && month <= 5)) {
      if (half === 1) addP('GCash', 1, `${year}-${monthStr}-30`, 285.56);
      else addP('GCash', 2, `${year}-${monthStr}-30`, 285.61);
    }

    // 7. Maya CC (18 mos: Nov 2026 - Apr 2028)
    if ((year === 2026 && month >= 11) || year === 2027 || (year === 2028 && month <= 4)) {
      if (half === 1) addP('Maya CC', 1, `${nextYear}-${nextMonthStr}-13`, 1500.00);
      else addP('Maya CC', 2, `${nextYear}-${nextMonthStr}-13`, 1500.00);
    }

    // 8. Atome Cash (Starts Feb 2027 per arrangement)
    if ((year === 2027 && month >= 2 && month <= 10)) {
      if (half === 1) addP('Atome Cash', 1, `${year}-${monthStr}-15`, 2677.50, 'Starts Feb 2027');
      else addP('Atome Cash', 2, `${year}-${monthStr}-15`, 2677.50, 'Starts Feb 2027');
    }

    // 9. Uno Bank (5 mos: Nov 2026 - Mar 2027)
    if ((year === 2026 && month >= 11) || (year === 2027 && month <= 3)) {
      if (half === 1) addP('Uno Bank', 1, `${nextYear}-${nextMonthStr}-01`, 2050.00);
      else addP('Uno Bank', 2, `${nextYear}-${nextMonthStr}-01`, 2050.00);
    }

    // 10. BDO CC (18 mos: Nov 2026 - Apr 2028)
    if ((year === 2026 && month >= 11) || year === 2027 || (year === 2028 && month <= 4)) {
      if (half === 1) addP('BDO CC', 1, `${nextYear}-${nextMonthStr}-14`, 500.00);
      else addP('BDO CC', 2, `${nextYear}-${nextMonthStr}-14`, 500.00);
    }

    // 11. Car (24 mos: Nov 2026 - Oct 2028)
    if ((year === 2026 && month >= 11) || (year <= 2028 && month <= 10)) {
      if (half === 1) addP('Car', 2, `${year}-${monthStr}-18`, 3625.00);
      else addP('Car', 1, `${nextYear}-${nextMonthStr}-18`, 3625.00);
    }
  });

  return payments;
};

// Helper for Currency Formatting
const formatPHP = (amount) => {
  return new Intl.NumberFormat('en-PH', {
    style: 'currency',
    currency: 'PHP',
    minimumFractionDigits: 2
  }).format(amount || 0).replace('PHP', '₱');
};

export default function App() {
  const [activeTab, setActiveTab] = useState('dashboard');
  const [lastSavedTime, setLastSavedTime] = useState('');

  // SAFE LOCAL STORAGE INITIALIZERS
  const [periods, setPeriods] = useState(() => {
    try {
      const saved = localStorage.getItem('rods_tracker_periods');
      if (saved) return JSON.parse(saved);
    } catch (e) {
      console.error('Failed to load periods from localStorage:', e);
    }
    return generateSalaryPeriods();
  });

  const [payments, setPayments] = useState(() => {
    try {
      const saved = localStorage.getItem('rods_tracker_payments');
      if (saved) return JSON.parse(saved);
    } catch (e) {
      console.error('Failed to load payments from localStorage:', e);
    }
    return generateInitialPayments(generateSalaryPeriods());
  });

  const [loans, setLoans] = useState(() => {
    try {
      const saved = localStorage.getItem('rods_tracker_loans');
      if (saved) return JSON.parse(saved);
    } catch (e) {
      console.error('Failed to load loans from localStorage:', e);
    }
    return INITIAL_LOANS;
  });

  // Selected Salary Period for Salary Input page
  const [selectedPeriodId, setSelectedPeriodId] = useState('2026-11-P1');

  // Filters & Search State for Payment Tracker
  const [trackerFilterStatus, setTrackerFilterStatus] = useState('ALL');
  const [trackerFilterLoan, setTrackerFilterLoan] = useState('ALL');
  const [trackerSearch, setTrackerSearch] = useState('');

  // New item modal
  const [isAddPaymentModalOpen, setIsAddPaymentModalOpen] = useState(false);
  const [newPayment, setNewPayment] = useState({
    loanName: 'TikTok',
    installmentNumber: 1,
    periodId: '2026-11-P1',
    dueDate: '2026-11-18',
    amount: 1000,
    remarks: ''
  });

  // IMMEDIATE EFFECT: PERSIST DATA UPON CHANGES
  useEffect(() => {
    try {
      localStorage.setItem('rods_tracker_periods', JSON.stringify(periods));
      localStorage.setItem('rods_tracker_payments', JSON.stringify(payments));
      localStorage.setItem('rods_tracker_loans', JSON.stringify(loans));
      setLastSavedTime(new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit', second: '2-digit' }));
    } catch (e) {
      console.error('Failed to persist to localStorage:', e);
    }
  }, [periods, payments, loans]);

  // Handle Marking Payment Paid / Pending
  const togglePaymentStatus = (paymentId) => {
    setPayments(prev => prev.map(pmt => {
      if (pmt.id === paymentId) {
        const isNowPaid = pmt.status !== 'PAID';
        return {
          ...pmt,
          status: isNowPaid ? 'PAID' : 'PENDING',
          paidDate: isNowPaid ? new Date().toISOString().split('T')[0] : null
        };
      }
      return pmt;
    }));
  };

  // Salary Update Handler
  const handleSalaryChange = (periodId, newSalary) => {
    setPeriods(prev => prev.map(p => p.id === periodId ? { ...p, salary: parseFloat(newSalary) || 0 } : p));
  };

  // Add Custom Payment Line Item
  const handleAddPayment = (e) => {
    e.preventDefault();
    const selectedPeriodObj = periods.find(p => p.id === newPayment.periodId) || periods[0];
    const newEntry = {
      id: `custom-pmt-${Date.now()}`,
      loanName: newPayment.loanName,
      installmentNumber: parseInt(newPayment.installmentNumber) || 1,
      periodId: newPayment.periodId,
      periodName: selectedPeriodObj.name,
      dueDate: newPayment.dueDate,
      amount: parseFloat(newPayment.amount) || 0,
      status: 'PENDING',
      paidDate: null,
      remarks: newPayment.remarks || 'Custom added payment'
    };

    setPayments(prev => [newEntry, ...prev]);
    setIsAddPaymentModalOpen(false);
  };

  // Metric Computations
  const globalMetrics = useMemo(() => {
    const totalScheduledAmount = payments.reduce((sum, p) => sum + p.amount, 0);
    const totalPaidAmount = payments.filter(p => p.status === 'PAID').reduce((sum, p) => sum + p.amount, 0);
    const remainingDebt = totalScheduledAmount - totalPaidAmount;
    
    const totalPaymentsCount = payments.length;
    const completedPaymentsCount = payments.filter(p => p.status === 'PAID').length;
    const pendingPaymentsCount = payments.filter(p => p.status === 'PENDING').length;
    
    const todayStr = new Date().toISOString().split('T')[0];
    const overdueCount = payments.filter(p => p.status === 'PENDING' && p.dueDate < todayStr).length;

    const completionRate = totalScheduledAmount > 0 ? (totalPaidAmount / totalScheduledAmount) * 100 : 0;

    return {
      totalScheduledAmount,
      totalPaidAmount,
      remainingDebt,
      totalPaymentsCount,
      completedPaymentsCount,
      pendingPaymentsCount,
      overdueCount,
      completionRate,
      activeLoansCount: loans.length
    };
  }, [payments, loans]);

  // Selected Salary Period Metrics
  const currentPeriodData = useMemo(() => {
    const periodObj = periods.find(p => p.id === selectedPeriodId) || periods[0];
    const periodPayments = payments.filter(p => p.periodId === selectedPeriodId);

    const salaryReceived = periodObj.salary || 0;
    const totalScheduledDebt = periodPayments.reduce((sum, p) => sum + p.amount, 0);
    const totalPaidDebt = periodPayments.filter(p => p.status === 'PAID').reduce((sum, p) => sum + p.amount, 0);
    const remainingUnpaidDebt = totalScheduledDebt - totalPaidDebt;
    
    const projectedRemainingSalary = salaryReceived - totalScheduledDebt;
    const actualAvailableBalance = salaryReceived - totalPaidDebt;
    
    const dtiRatio = salaryReceived > 0 ? (totalScheduledDebt / salaryReceived) * 100 : 0;
    const periodCompletionRate = totalScheduledDebt > 0 ? (totalPaidDebt / totalScheduledDebt) * 100 : 0;

    return {
      periodObj,
      periodPayments,
      salaryReceived,
      totalScheduledDebt,
      totalPaidDebt,
      remainingUnpaidDebt,
      projectedRemainingSalary,
      actualAvailableBalance,
      dtiRatio,
      periodCompletionRate
    };
  }, [selectedPeriodId, periods, payments]);

  // Reset Application Data
  const handleResetData = () => {
    if (window.confirm("Are you sure you want to reset all data back to the default schedule? Any saved checkmarks or custom entries will be restored to defaults.")) {
      const defaultPeriods = generateSalaryPeriods();
      const defaultPayments = generateInitialPayments(defaultPeriods);
      setPeriods(defaultPeriods);
      setPayments(defaultPayments);
      setLoans(INITIAL_LOANS);
      localStorage.removeItem('rods_tracker_periods');
      localStorage.removeItem('rods_tracker_payments');
      localStorage.removeItem('rods_tracker_loans');
    }
  };

  // Export CSV
  const handleExportCSV = () => {
    let csvContent = "data:text/csv;charset=utf-8,";
    csvContent += "ID,Loan Name,Installment,Salary Period,Due Date,Amount,Status,Date Paid,Remarks\n";
    payments.forEach(p => {
      csvContent += `"${p.id}","${p.loanName}","${p.installmentNumber}","${p.periodName}","${p.dueDate}",${p.amount},"${p.status}","${p.paidDate || ''}","${p.remarks || ''}"\n`;
    });
    const encodedUri = encodeURI(csvContent);
    const link = document.createElement("a");
    link.setAttribute("href", encodedUri);
    link.setAttribute("download", `rods_tracker_schedule.csv`);
    document.body.appendChild(link);
    link.click();
    link.remove();
  };

  return (
    <div className="min-h-screen bg-[#fbfbfa] text-[#1c1d1f] font-sans antialiased flex flex-col md:flex-row">
      {/* SIDEBAR NAVIGATION */}
      <aside className="w-full md:w-64 bg-[#f2f0eb] border-r border-stone-200 p-5 flex flex-col justify-between shrink-0">
        <div>
          {/* Logo Brand Header */}
          <div className="flex items-center gap-3 px-2 py-3 mb-6">
            <div className="bg-[#5a7865] text-white p-2.5 rounded-xl shadow-sm">
              <ShieldCheck className="w-6 h-6" />
            </div>
            <div>
              <h1 className="font-bold text-lg tracking-tight text-[#1c1d1f]">Rod's Tracker</h1>
              <p className="text-xs text-stone-500 font-medium">Debt & Salary Allocator</p>
            </div>
          </div>

          {/* Navigation Links */}
          <nav className="space-y-1">
            {[
              { id: 'dashboard', label: 'Dashboard', icon: LayoutDashboard },
              { id: 'tracker', label: 'Debt Tracker', icon: CheckSquare },
              { id: 'salary', label: 'Salary Input', icon: Wallet },
              { id: 'loans', label: 'Loan Management', icon: CreditCard },
              { id: 'analytics', label: 'Analytics & Summary', icon: BarChart3 },
              { id: 'calendar', label: 'Payment Calendar', icon: CalendarIcon },
            ].map(item => {
              const Icon = item.icon;
              const isActive = activeTab === item.id;
              return (
                <button
                  key={item.id}
                  onClick={() => setActiveTab(item.id)}
                  className={`w-full flex items-center gap-3 px-3.5 py-2.5 rounded-xl font-medium text-sm transition-all duration-200 ${
                    isActive 
                      ? 'bg-[#5a7865] text-white shadow-sm' 
                      : 'text-stone-600 hover:bg-stone-200/60 hover:text-stone-900'
                  }`}
                >
                  <Icon className="w-4 h-4" />
                  {item.label}
                </button>
              );
            })}
          </nav>
        </div>

        {/* Quick System Tools Bottom */}
        <div className="pt-6 border-t border-stone-300/60 mt-6 space-y-2">
          <div className="px-2 mb-2 flex items-center justify-between">
            <p className="text-[10px] uppercase tracking-wider text-stone-500 font-semibold">Persistence State</p>
            {lastSavedTime && (
              <span className="text-[10px] text-[#5a7865] font-semibold flex items-center gap-1">
                <Save className="w-3 h-3" /> Saved {lastSavedTime}
              </span>
            )}
          </div>
          <button 
            onClick={handleExportCSV}
            className="w-full flex items-center justify-between px-3 py-2 text-xs font-medium text-stone-700 bg-white border border-stone-200 rounded-lg hover:bg-stone-100 transition"
          >
            <span className="flex items-center gap-2"><Download className="w-3.5 h-3.5" /> Export Schedule CSV</span>
          </button>
          <button 
            onClick={handleResetData}
            className="w-full flex items-center justify-between px-3 py-2 text-xs font-medium text-amber-700 bg-amber-50 border border-amber-200 rounded-lg hover:bg-amber-100 transition"
          >
            <span className="flex items-center gap-2"><RotateCcw className="w-3.5 h-3.5" /> Restore Default Schedule</span>
          </button>
        </div>
      </aside>

      {/* MAIN CONTENT AREA */}
      <main className="flex-1 overflow-y-auto p-4 md:p-8 space-y-6">
        {/* HEADER BAR */}
        <header className="flex flex-col sm:flex-row sm:items-center justify-between gap-4 pb-4 border-b border-stone-200">
          <div>
            <span className="text-xs font-semibold uppercase tracking-wider text-[#5a7865]">Personal Financial System</span>
            <h2 className="text-2xl font-bold tracking-tight capitalize text-[#1c1d1f]">
              {activeTab === 'dashboard' && 'Financial Dashboard'}
              {activeTab === 'tracker' && 'Debt Payment Schedule (Source of Truth)'}
              {activeTab === 'salary' && 'Salary Allocation & Cutoffs'}
              {activeTab === 'loans' && 'Active Loan Portfolio'}
              {activeTab === 'analytics' && 'Financial Analytics & Trends'}
              {activeTab === 'calendar' && 'Interactive Schedule Calendar'}
            </h2>
          </div>

          <div className="flex items-center gap-3">
            <div className="bg-white border border-stone-200 rounded-xl px-4 py-2 flex items-center gap-3 shadow-xs">
              <div className="text-right">
                <p className="text-[10px] uppercase tracking-wider text-stone-500 font-bold">Overall Progress</p>
                <p className="text-sm font-bold text-[#5a7865]">{globalMetrics.completionRate.toFixed(1)}% Paid</p>
              </div>
              <div className="w-10 h-10 rounded-full bg-[#5a7865]/10 flex items-center justify-center text-[#5a7865] font-bold text-xs">
                {Math.round(globalMetrics.completionRate)}%
              </div>
            </div>
          </div>
        </header>

        {/* 1. DASHBOARD PAGE */}
        {activeTab === 'dashboard' && (
          <div className="space-y-6">
            <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <div className="flex items-center justify-between text-stone-500 mb-2">
                  <span className="text-xs font-medium">Total Scheduled Debt</span>
                  <DollarSign className="w-4 h-4 text-stone-400" />
                </div>
                <p className="text-2xl font-bold text-[#1c1d1f]">{formatPHP(globalMetrics.totalScheduledAmount)}</p>
                <p className="text-xs text-stone-500 mt-1">Across 281 payment entries</p>
              </div>

              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <div className="flex items-center justify-between text-stone-500 mb-2">
                  <span className="text-xs font-medium">Total Debt Paid</span>
                  <CheckCircle2 className="w-4 h-4 text-[#5a7865]" />
                </div>
                <p className="text-2xl font-bold text-[#5a7865]">{formatPHP(globalMetrics.totalPaidAmount)}</p>
                <div className="w-full bg-stone-100 rounded-full h-1.5 mt-3 overflow-hidden">
                  <div className="bg-[#5a7865] h-full rounded-full" style={{ width: `${globalMetrics.completionRate}%` }}></div>
                </div>
              </div>

              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <div className="flex items-center justify-between text-stone-500 mb-2">
                  <span className="text-xs font-medium">Remaining Debt</span>
                  <Clock className="w-4 h-4 text-[#4a6b82]" />
                </div>
                <p className="text-2xl font-bold text-[#4a6b82]">{formatPHP(globalMetrics.remainingDebt)}</p>
                <p className="text-xs text-stone-500 mt-1">{globalMetrics.pendingPaymentsCount} pending line items</p>
              </div>

              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <div className="flex items-center justify-between text-stone-500 mb-2">
                  <span className="text-xs font-medium">Active Loans</span>
                  <Building2 className="w-4 h-4 text-stone-400" />
                </div>
                <p className="text-2xl font-bold text-[#1c1d1f]">{globalMetrics.activeLoansCount}</p>
                <p className="text-xs text-stone-500 mt-1">Across 52 salary cutoffs</p>
              </div>
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
              <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs flex flex-col justify-between">
                <div>
                  <h3 className="text-base font-bold text-[#1c1d1f] mb-1">Debt Repayment Status</h3>
                  <p className="text-xs text-stone-500 mb-6">Paid vs remaining total obligations</p>
                </div>
                
                <div className="flex flex-col items-center justify-center my-4">
                  <div 
                    className="w-44 h-44 rounded-full flex items-center justify-center relative shadow-inner transition-all"
                    style={{
                      background: `conic-gradient(#5a7865 0% ${globalMetrics.completionRate}%, #e5e7eb ${globalMetrics.completionRate}% 100%)`
                    }}
                  >
                    <div className="w-32 h-32 bg-white rounded-full flex flex-col items-center justify-center shadow-xs">
                      <span className="text-2xl font-extrabold text-[#1c1d1f]">{globalMetrics.completionRate.toFixed(1)}%</span>
                      <span className="text-[11px] font-semibold text-stone-500 uppercase tracking-wider">Completed</span>
                    </div>
                  </div>
                </div>

                <div className="grid grid-cols-2 gap-4 pt-4 border-t border-stone-100 text-center">
                  <div>
                    <span className="inline-block w-2.5 h-2.5 rounded-full bg-[#5a7865] mr-1.5"></span>
                    <span className="text-xs text-stone-500">Paid:</span>
                    <p className="text-sm font-bold text-[#5a7865]">{formatPHP(globalMetrics.totalPaidAmount)}</p>
                  </div>
                  <div>
                    <span className="inline-block w-2.5 h-2.5 rounded-full bg-stone-300 mr-1.5"></span>
                    <span className="text-xs text-stone-500">Remaining:</span>
                    <p className="text-sm font-bold text-stone-700">{formatPHP(globalMetrics.remainingDebt)}</p>
                  </div>
                </div>
              </div>

              <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs lg:col-span-2">
                <h3 className="text-base font-bold text-[#1c1d1f] mb-1">Loan Contribution Breakdown</h3>
                <p className="text-xs text-stone-500 mb-6">Total financial weight per biller</p>
                <div className="space-y-4 max-h-[300px] overflow-y-auto pr-2">
                  {loans.map(loan => {
                    const loanTotal = payments.filter(p => p.loanName === loan.name).reduce((s, p) => s + p.amount, 0);
                    const loanPaid = payments.filter(p => p.loanName === loan.name && p.status === 'PAID').reduce((s, p) => s + p.amount, 0);
                    const pct = loanTotal > 0 ? (loanPaid / loanTotal) * 100 : 0;
                    return (
                      <div key={loan.id} className="space-y-1">
                        <div className="flex justify-between text-xs">
                          <span className="font-semibold text-stone-800">{loan.name} ({loan.splits === 2 ? '2 Splits' : '1 Split'})</span>
                          <span className="text-stone-500">{formatPHP(loanPaid)} / {formatPHP(loanTotal)} ({pct.toFixed(0)}%)</span>
                        </div>
                        <div className="w-full bg-stone-100 rounded-full h-2 overflow-hidden flex">
                          <div className="bg-[#5a7865] h-full transition-all duration-300" style={{ width: `${pct}%` }}></div>
                        </div>
                      </div>
                    );
                  })}
                </div>
              </div>
            </div>

            <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs">
              <div className="flex items-center justify-between mb-4">
                <div>
                  <h3 className="text-base font-bold text-[#1c1d1f]">Upcoming Obligations Feed</h3>
                  <p className="text-xs text-stone-500">Next scheduled payments requiring attention</p>
                </div>
                <button onClick={() => setActiveTab('tracker')} className="text-xs font-semibold text-[#5a7865] hover:underline flex items-center gap-1">
                  View All Schedule <ChevronRight className="w-3.5 h-3.5" />
                </button>
              </div>

              <div className="divide-y divide-stone-100">
                {payments.filter(p => p.status === 'PENDING').slice(0, 5).map(pmt => (
                  <div key={pmt.id} className="py-3 flex items-center justify-between gap-4">
                    <div className="flex items-center gap-3">
                      <div className="w-9 h-9 rounded-xl bg-stone-100 flex items-center justify-center text-stone-600 font-bold text-xs">
                        #{pmt.installmentNumber}
                      </div>
                      <div>
                        <h4 className="text-sm font-semibold text-stone-900">{pmt.loanName} {pmt.installmentNumber}</h4>
                        <p className="text-xs text-stone-500">{pmt.periodName} • Due: <span className="font-medium text-stone-700">{formatAlphaDate(pmt.dueDate)}</span></p>
                      </div>
                    </div>
                    <div className="flex items-center gap-4">
                      <span className="text-sm font-bold text-stone-900">{formatPHP(pmt.amount)}</span>
                      <button 
                        onClick={() => togglePaymentStatus(pmt.id)}
                        className="px-3 py-1.5 text-xs font-medium rounded-lg bg-[#5a7865]/10 text-[#5a7865] hover:bg-[#5a7865] hover:text-white transition"
                      >
                        Mark Paid
                      </button>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {/* 2. DEBT TRACKER PAGE (SOURCE OF TRUTH) */}
        {activeTab === 'tracker' && (
          <div className="space-y-6">
            <div className="bg-white p-4 rounded-2xl border border-stone-200 shadow-xs flex flex-col md:flex-row gap-4 items-center justify-between">
              <div className="relative w-full md:w-72">
                <Search className="w-4 h-4 absolute left-3 top-3 text-stone-400" />
                <input
                  type="text"
                  placeholder="Search loan or period..."
                  value={trackerSearch}
                  onChange={(e) => setTrackerSearch(e.target.value)}
                  className="w-full pl-9 pr-4 py-2 bg-stone-50 border border-stone-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-[#5a7865]"
                />
              </div>

              <div className="flex items-center gap-1 bg-stone-100 p-1 rounded-xl w-full md:w-auto">
                {['ALL', 'PENDING', 'PAID'].map(st => (
                  <button
                    key={st}
                    onClick={() => setTrackerFilterStatus(st)}
                    className={`px-3 py-1.5 rounded-lg text-xs font-semibold transition ${
                      trackerFilterStatus === st ? 'bg-white text-stone-900 shadow-xs' : 'text-stone-500 hover:text-stone-900'
                    }`}
                  >
                    {st}
                  </button>
                ))}
              </div>

              <div className="flex items-center gap-3 w-full md:w-auto">
                <select
                  value={trackerFilterLoan}
                  onChange={(e) => setTrackerFilterLoan(e.target.value)}
                  className="py-2 px-3 bg-stone-50 border border-stone-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-[#5a7865]"
                >
                  <option value="ALL">All Biller Loans</option>
                  {loans.map(l => (
                    <option key={l.id} value={l.name}>{l.name}</option>
                  ))}
                </select>

                <button
                  onClick={() => setIsAddPaymentModalOpen(true)}
                  className="px-3.5 py-2 bg-[#5a7865] text-white rounded-xl text-xs font-semibold hover:bg-[#4a6554] transition flex items-center gap-1.5 shrink-0"
                >
                  <Plus className="w-4 h-4" /> Add Payment Line
                </button>
              </div>
            </div>

            {/* Source of Truth Table */}
            <div className="bg-white rounded-2xl border border-stone-200 shadow-xs overflow-hidden">
              <div className="overflow-x-auto max-h-[70vh] overflow-y-auto">
                <table className="w-full text-left border-collapse relative">
                  <thead className="sticky top-0 z-10">
                    <tr className="bg-stone-100 border-b border-stone-200 text-[11px] uppercase tracking-wider text-stone-600 font-semibold shadow-xs">
                      <th className="py-3.5 px-4 text-center">Status</th>
                      <th className="py-3.5 px-4">Loan Name</th>
                      <th className="py-3.5 px-4">Installment</th>
                      <th className="py-3.5 px-4">Salary Period</th>
                      <th className="py-3.5 px-4">Actual Due Date</th>
                      <th className="py-3.5 px-4 text-right">Scheduled Amount</th>
                      <th className="py-3.5 px-4">Date Paid</th>
                      <th className="py-3.5 px-4">Remarks</th>
                    </tr>
                  </thead>
                  <tbody className="divide-y divide-stone-100 text-xs">
                    {payments
                      .filter(p => {
                        const matchesStatus = trackerFilterStatus === 'ALL' || p.status === trackerFilterStatus;
                        const matchesLoan = trackerFilterLoan === 'ALL' || p.loanName === trackerFilterLoan;
                        const matchesSearch = p.loanName.toLowerCase().includes(trackerSearch.toLowerCase()) || p.periodName.toLowerCase().includes(trackerSearch.toLowerCase());
                        return matchesStatus && matchesLoan && matchesSearch;
                      })
                      .map((pmt) => {
                        const isPaid = pmt.status === 'PAID';
                        return (
                          <tr key={pmt.id} className={`hover:bg-stone-50/60 transition ${isPaid ? 'bg-stone-50/30' : ''}`}>
                            <td className="py-3 px-4 text-center">
                              <input 
                                type="checkbox"
                                checked={isPaid}
                                onChange={() => togglePaymentStatus(pmt.id)}
                                className="w-4 h-4 rounded text-[#5a7865] focus:ring-[#5a7865] cursor-pointer"
                              />
                            </td>
                            <td className="py-3 px-4 font-bold text-stone-900">{pmt.loanName}</td>
                            <td className="py-3 px-4 font-medium text-stone-600">
                              <span className="px-2 py-0.5 bg-stone-100 rounded text-[10px] font-semibold text-stone-700">Split #{pmt.installmentNumber}</span>
                            </td>
                            <td className="py-3 px-4 font-medium text-stone-600">{pmt.periodName}</td>
                            <td className="py-3 px-4 font-semibold text-[#4a6b82]">{formatAlphaDate(pmt.dueDate)}</td>
                            <td className="py-3 px-4 text-right font-bold text-stone-900">{formatPHP(pmt.amount)}</td>
                            <td className="py-3 px-4 text-stone-500">{pmt.paidDate ? formatAlphaDate(pmt.paidDate) : '-'}</td>
                            <td className="py-3 px-4 text-stone-500 italic max-w-xs truncate">{pmt.remarks}</td>
                          </tr>
                        );
                      })}
                  </tbody>
                </table>
              </div>
              <div className="p-3 bg-stone-50 border-t border-stone-200 text-center text-xs text-stone-500 font-medium">
                Master Ledger View: Checkboxes instantly persist state changes into local storage.
              </div>
            </div>
          </div>
        )}

        {/* Modal for Adding Custom Line Item */}
        {isAddPaymentModalOpen && (
          <div className="fixed inset-0 bg-black/40 backdrop-blur-xs flex items-center justify-center p-4 z-50">
            <div className="bg-white p-6 rounded-2xl max-w-md w-full space-y-4 shadow-xl">
              <h3 className="text-lg font-bold text-stone-900">Add Payment Schedule Entry</h3>
              <form onSubmit={handleAddPayment} className="space-y-3 text-xs">
                <div>
                  <label className="font-semibold block mb-1">Loan / Biller Name</label>
                  <input
                    type="text"
                    required
                    value={newPayment.loanName}
                    onChange={(e) => setNewPayment({ ...newPayment, loanName: e.target.value })}
                    className="w-full p-2.5 border border-stone-300 rounded-xl"
                  />
                </div>
                <div>
                  <label className="font-semibold block mb-1">Installment Number</label>
                  <input
                    type="number"
                    required
                    value={newPayment.installmentNumber}
                    onChange={(e) => setNewPayment({ ...newPayment, installmentNumber: e.target.value })}
                    className="w-full p-2.5 border border-stone-300 rounded-xl"
                  />
                </div>
                <div>
                  <label className="font-semibold block mb-1">Salary Period Cutoff</label>
                  <select
                    value={newPayment.periodId}
                    onChange={(e) => setNewPayment({ ...newPayment, periodId: e.target.value })}
                    className="w-full p-2.5 border border-stone-300 rounded-xl"
                  >
                    {periods.map(p => (
                      <option key={p.id} value={p.id}>{p.name}</option>
                    ))}
                  </select>
                </div>
                <div>
                  <label className="font-semibold block mb-1">Actual Loan Due Date</label>
                  <input
                    type="date"
                    required
                    value={newPayment.dueDate}
                    onChange={(e) => setNewPayment({ ...newPayment, dueDate: e.target.value })}
                    className="w-full p-2.5 border border-stone-300 rounded-xl"
                  />
                </div>
                <div>
                  <label className="font-semibold block mb-1">Amount (₱)</label>
                  <input
                    type="number"
                    step="0.01"
                    required
                    value={newPayment.amount}
                    onChange={(e) => setNewPayment({ ...newPayment, amount: e.target.value })}
                    className="w-full p-2.5 border border-stone-300 rounded-xl"
                  />
                </div>
                <div>
                  <label className="font-semibold block mb-1">Remarks</label>
                  <input
                    type="text"
                    value={newPayment.remarks}
                    onChange={(e) => setNewPayment({ ...newPayment, remarks: e.target.value })}
                    className="w-full p-2.5 border border-stone-300 rounded-xl"
                  />
                </div>
                <div className="flex gap-2 pt-2">
                  <button
                    type="button"
                    onClick={() => setIsAddPaymentModalOpen(false)}
                    className="w-1/2 py-2.5 bg-stone-100 text-stone-700 font-semibold rounded-xl"
                  >
                    Cancel
                  </button>
                  <button
                    type="submit"
                    className="w-1/2 py-2.5 bg-[#5a7865] text-white font-semibold rounded-xl"
                  >
                    Save Entry
                  </button>
                </div>
              </form>
            </div>
          </div>
        )}

        {/* 3. SALARY INPUT PAGE */}
        {activeTab === 'salary' && (
          <div className="space-y-6">
            <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
              <div>
                <label className="text-xs font-semibold uppercase tracking-wider text-stone-500 block mb-1">Select Payroll Cutoff Period</label>
                <select
                  value={selectedPeriodId}
                  onChange={(e) => setSelectedPeriodId(e.target.value)}
                  className="py-2.5 px-4 bg-stone-50 border border-stone-300 rounded-xl text-base font-bold text-stone-900 focus:outline-none focus:ring-2 focus:ring-[#5a7865]"
                >
                  {periods.map(p => (
                    <option key={p.id} value={p.id}>{p.name}</option>
                  ))}
                </select>
              </div>

              <div className="w-full md:w-auto">
                <label className="text-xs font-semibold uppercase tracking-wider text-stone-500 block mb-1">Salary Input for Period (₱)</label>
                <div className="relative">
                  <span className="absolute left-3.5 top-2.5 text-stone-500 font-bold">₱</span>
                  <input
                    type="number"
                    value={currentPeriodData.salaryReceived}
                    onChange={(e) => handleSalaryChange(selectedPeriodId, e.target.value)}
                    className="pl-8 pr-4 py-2 bg-stone-50 border border-stone-300 rounded-xl font-bold text-stone-900 text-lg w-full md:w-48 focus:outline-none focus:ring-2 focus:ring-[#5a7865]"
                  />
                </div>
              </div>
            </div>

            <div className="bg-[#4a6b82]/10 border border-[#4a6b82]/20 p-4 rounded-2xl flex items-start gap-3">
              <Info className="w-5 h-5 text-[#4a6b82] shrink-0 mt-0.5" />
              <div className="text-xs text-[#3b576c] space-y-1">
                <p className="font-bold">Projected Remaining Salary vs. Actual Available Balance</p>
                <p>
                  <strong>Projected Remaining Salary</strong> deducts <em>ALL</em> scheduled debts for this cutoff regardless of payment status (giving you a realistic budgeting view).
                  <strong> Actual Available Balance</strong> only deducts debts marked as <em>PAID</em>.
                </p>
              </div>
            </div>

            <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <p className="text-xs font-semibold text-stone-500">Salary Received</p>
                <p className="text-2xl font-bold text-stone-900 mt-1">{formatPHP(currentPeriodData.salaryReceived)}</p>
                <p className="text-[11px] text-stone-400 mt-1">Base income for cutoff</p>
              </div>

              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <p className="text-xs font-semibold text-stone-500">Total Scheduled Debt</p>
                <p className="text-2xl font-bold text-amber-600 mt-1">{formatPHP(currentPeriodData.totalScheduledDebt)}</p>
                <p className="text-[11px] text-stone-400 mt-1">DTI: {currentPeriodData.dtiRatio.toFixed(1)}%</p>
              </div>

              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <p className="text-xs font-semibold text-stone-500">Projected Remaining Salary</p>
                <p className={`text-2xl font-bold mt-1 ${currentPeriodData.projectedRemainingSalary >= 0 ? 'text-[#5a7865]' : 'text-rose-600'}`}>
                  {formatPHP(currentPeriodData.projectedRemainingSalary)}
                </p>
                <p className="text-[11px] text-stone-400 mt-1">After ALL period obligations</p>
              </div>

              <div className="bg-white p-5 rounded-2xl border border-stone-200 shadow-xs">
                <p className="text-xs font-semibold text-stone-500">Actual Available Balance</p>
                <p className="text-2xl font-bold text-[#4a6b82] mt-1">{formatPHP(currentPeriodData.actualAvailableBalance)}</p>
                <p className="text-[11px] text-stone-400 mt-1">Cash remaining today</p>
              </div>
            </div>

            <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs">
              <h3 className="text-base font-bold text-stone-900 mb-1">
                Assigned Debt Obligations for {currentPeriodData.periodObj.name}
              </h3>
              <p className="text-xs text-stone-500 mb-4">Toggle payments to see live updates to your actual balance.</p>

              <div className="space-y-3">
                {currentPeriodData.periodPayments.length === 0 ? (
                  <p className="text-xs text-stone-500 italic py-4 text-center">No debt payments assigned to this period.</p>
                ) : (
                  currentPeriodData.periodPayments.map(pmt => (
                    <div 
                      key={pmt.id} 
                      className={`p-4 rounded-xl border transition flex items-center justify-between gap-4 ${
                        pmt.status === 'PAID' ? 'bg-[#5a7865]/5 border-[#5a7865]/30' : 'bg-stone-50 border-stone-200'
                      }`}
                    >
                      <div className="flex items-center gap-3">
                        <input 
                          type="checkbox"
                          checked={pmt.status === 'PAID'}
                          onChange={() => togglePaymentStatus(pmt.id)}
                          className="w-5 h-5 rounded text-[#5a7865] focus:ring-[#5a7865] cursor-pointer"
                        />
                        <div>
                          <p className="text-sm font-bold text-stone-900">{pmt.loanName} {pmt.installmentNumber}</p>
                          <p className="text-xs text-stone-500">Actual Due Date: <span className="font-semibold text-stone-700">{formatAlphaDate(pmt.dueDate)}</span></p>
                        </div>
                      </div>
                      <div className="text-right">
                        <p className="text-base font-bold text-stone-900">{formatPHP(pmt.amount)}</p>
                        <span className={`inline-block px-2 py-0.5 rounded text-[10px] font-bold ${
                          pmt.status === 'PAID' ? 'bg-[#5a7865] text-white' : 'bg-amber-100 text-amber-800'
                        }`}>
                          {pmt.status}
                        </span>
                      </div>
                    </div>
                  ))
                )}
              </div>
            </div>
          </div>
        )}

        {/* 4. LOAN MANAGEMENT PAGE */}
        {activeTab === 'loans' && (
          <div className="space-y-6">
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
              {loans.map(loan => {
                const loanPmts = payments.filter(p => p.loanName === loan.name);
                const totalPaid = loanPmts.filter(p => p.status === 'PAID').reduce((s, p) => s + p.amount, 0);
                const totalScheduled = loanPmts.reduce((s, p) => s + p.amount, 0);
                const remaining = totalScheduled - totalPaid;
                const completionPct = totalScheduled > 0 ? (totalPaid / totalScheduled) * 100 : 0;

                return (
                  <div key={loan.id} className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs flex flex-col justify-between">
                    <div>
                      <div className="flex items-center justify-between mb-4">
                        <div className="p-2.5 rounded-xl bg-stone-100 text-[#5a7865]">
                          <Building2 className="w-5 h-5" />
                        </div>
                        <span className="text-xs font-bold text-[#4a6b82] bg-[#4a6b82]/10 px-2.5 py-1 rounded-full">
                          {loan.splits === 2 ? '2 Bi-Monthly Splits' : 'Single Period Split'}
                        </span>
                      </div>

                      <h3 className="text-lg font-bold text-stone-900">{loan.name}</h3>
                      <p className="text-xs text-stone-500 mb-4">Payoff Date: <span className="font-semibold text-stone-700">{formatAlphaDate(loan.payoffDate)}</span></p>

                      <div className="space-y-2 text-xs mb-4">
                        <div className="flex justify-between">
                          <span className="text-stone-500">Monthly Obligation:</span>
                          <span className="font-bold text-stone-900">{formatPHP(loan.monthlyAmount)}</span>
                        </div>
                        <div className="flex justify-between">
                          <span className="text-stone-500">Total Paid:</span>
                          <span className="font-bold text-[#5a7865]">{formatPHP(totalPaid)}</span>
                        </div>
                        <div className="flex justify-between">
                          <span className="text-stone-500">Remaining Balance:</span>
                          <span className="font-bold text-stone-700">{formatPHP(remaining)}</span>
                        </div>
                      </div>
                    </div>

                    <div>
                      <div className="flex justify-between text-xs font-semibold mb-1">
                        <span className="text-stone-500">Payoff Progress</span>
                        <span className="text-[#5a7865]">{completionPct.toFixed(1)}%</span>
                      </div>
                      <div className="w-full bg-stone-100 rounded-full h-2 overflow-hidden">
                        <div className="bg-[#5a7865] h-full rounded-full transition-all" style={{ width: `${completionPct}%` }}></div>
                      </div>
                    </div>
                  </div>
                );
              })}
            </div>
          </div>
        )}

        {/* 5. ANALYTICS & SUMMARY */}
        {activeTab === 'analytics' && (
          <div className="space-y-6">
            <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs">
              <h3 className="text-base font-bold text-stone-900 mb-2">Bi-Monthly Outflow Distribution</h3>
              <p className="text-xs text-stone-500 mb-6">Visualizing debt obligation weight per period</p>
              
              <div className="h-64 flex items-end gap-2 pt-6 pb-2 px-2 border-b border-stone-200 overflow-x-auto">
                {periods.slice(0, 15).map(p => {
                  const pTotal = payments.filter(pmt => pmt.periodId === p.id).reduce((s, pmt) => s + pmt.amount, 0);
                  const heightPct = Math.min((pTotal / 25000) * 100, 100);
                  return (
                    <div key={p.id} className="flex-1 flex flex-col items-center gap-2 min-w-[40px]">
                      <span className="text-[10px] font-bold text-stone-600">₱{(pTotal / 1000).toFixed(1)}k</span>
                      <div className="w-full bg-[#5a7865]/20 rounded-t-md hover:bg-[#5a7865] transition-all relative group" style={{ height: `${heightPct}%` }}>
                        <div className="bg-[#5a7865] w-full bottom-0 absolute rounded-t-md" style={{ height: '100%' }}></div>
                      </div>
                      <span className="text-[9px] text-stone-400 rotate-45 origin-left whitespace-nowrap mt-2">{p.name.split(',')[0]}</span>
                    </div>
                  );
                })}
              </div>
            </div>
          </div>
        )}

        {/* 6. PAYMENT CALENDAR */}
        {activeTab === 'calendar' && (
          <div className="bg-white p-6 rounded-2xl border border-stone-200 shadow-xs space-y-4">
            <div className="flex justify-between items-center">
              <h3 className="text-base font-bold text-stone-900">Debt Schedule Timeline</h3>
              <span className="text-xs text-stone-500 font-semibold">2026 – 2028 Horizon ({payments.length} Scheduled Payments)</span>
            </div>
            
            <div className="divide-y divide-stone-100 max-h-[70vh] overflow-y-auto pr-2">
              {payments.map(pmt => (
                <div key={pmt.id} className="py-3 flex items-center justify-between hover:bg-stone-50/60 px-2 rounded-lg transition">
                  <div>
                    <p className="text-sm font-bold text-stone-900">{pmt.loanName} {pmt.installmentNumber}</p>
                    <p className="text-xs text-stone-500">Period: {pmt.periodName} | Due: <span className="text-[#4a6b82] font-semibold">{formatAlphaDate(pmt.dueDate)}</span></p>
                  </div>
                  <div className="text-right">
                    <p className="text-sm font-bold text-stone-900">{formatPHP(pmt.amount)}</p>
                    <span className={`text-[10px] font-bold px-2 py-0.5 rounded ${pmt.status === 'PAID' ? 'bg-[#5a7865]/10 text-[#5a7865]' : 'bg-amber-100 text-amber-800'}`}>
                      {pmt.status}
                    </span>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}
      </main>
    </div>
  );
}