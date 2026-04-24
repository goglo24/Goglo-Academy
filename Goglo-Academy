```react
import React, { useState, useEffect, useMemo } from 'react';
import { 
  BookOpen, 
  PlayCircle, 
  FileText, 
  CheckCircle, 
  Download, 
  User, 
  ChevronRight, 
  Search,
  ArrowLeft,
  Clock,
  Lock,
  Phone,
  LogOut,
  DownloadCloud
} from 'lucide-react';

/**
 * Goglo-Academy Mobile Application
 * Features: Video Lessons, PDF Materials, Practice Exams, Offline Access UI
 */

const App = () => {
  // State Management
  const [user, setUser] = useState(null);
  const [view, setView] = useState('home'); // home, lessons, pdfs, exams, profile, lesson-detail, exam-session
  const [searchQuery, setSearchQuery] = useState('');
  const [selectedItem, setSelectedItem] = useState(null);
  const [authForm, setAuthForm] = useState({ phone: '', password: '' });
  const [isOfflineMode, setIsOfflineMode] = useState(false);

  // Mock Data
  const categories = ['Mathematics', 'Physics', 'Chemistry', 'Biology', 'English'];
  
  const lessons = [
    { id: 1, title: 'Calculus Fundamentals', category: 'Mathematics', duration: '45 mins', instructor: 'Dr. Sarah', thumbnail: 'https://images.unsplash.com/photo-1635070041078-e363dbe005cb?auto=format&fit=crop&q=80&w=400', progress: 80 },
    { id: 2, title: 'Quantum Mechanics Intro', category: 'Physics', duration: '32 mins', instructor: 'Prof. James', thumbnail: 'https://images.unsplash.com/photo-1636466497217-26a8cbeaf0aa?auto=format&fit=crop&q=80&w=400', progress: 30 },
    { id: 3, title: 'Organic Chemistry Bonds', category: 'Chemistry', duration: '50 mins', instructor: 'Dr. Lee', thumbnail: 'https://images.unsplash.com/photo-1532187863486-abf91ad1b26d?auto=format&fit=crop&q=80&w=400', progress: 0 },
  ];

  const pdfs = [
    { id: 1, title: 'Entrance Exam Formula Sheet', size: '2.4 MB', category: 'Mathematics' },
    { id: 2, title: 'Physics Lab Notes', size: '5.1 MB', category: 'Physics' },
    { id: 3, title: 'Chemistry Periodic Table Guide', size: '1.8 MB', category: 'Chemistry' },
  ];

  const exams = [
    { id: 1, title: 'Full Mock Exam 2024', questions: 50, time: '60 mins', difficulty: 'Hard' },
    { id: 2, title: 'Math Speed Test', questions: 20, time: '15 mins', difficulty: 'Medium' },
  ];

  // Auth Logic
  const handleLogin = (e) => {
    e.preventDefault();
    if (authForm.phone && authForm.password) {
      setUser({ name: 'Future Scholar', phone: authForm.phone });
    }
  };

  // Components
  const ProgressBar = ({ value }) => (
    <div className="w-full bg-gray-200 rounded-full h-1.5 mt-2">
      <div className="bg-indigo-600 h-1.5 rounded-full" style={{ width: `${value}%` }}></div>
    </div>
  );

  const BottomNav = () => (
    <nav className="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-200 flex justify-around items-center p-3 z-50">
      {[
        { id: 'home', icon: BookOpen, label: 'Learn' },
        { id: 'lessons', icon: PlayCircle, label: 'Videos' },
        { id: 'pdfs', icon: FileText, label: 'Docs' },
        { id: 'profile', icon: User, label: 'Me' },
      ].map((item) => (
        <button
          key={item.id}
          onClick={() => setView(item.id)}
          className={`flex flex-col items-center gap-1 ${view === item.id ? 'text-indigo-600' : 'text-gray-400'}`}
        >
          <item.icon size={22} strokeWidth={view === item.id ? 2.5 : 2} />
          <span className="text-[10px] font-medium">{item.label}</span>
        </button>
      ))}
    </nav>
  );

  // View Controllers
  if (!user) {
    return (
      <div className="min-h-screen bg-slate-50 flex flex-col items-center justify-center p-6 font-sans">
        <div className="w-full max-w-sm space-y-8">
          <div className="text-center">
            <div className="inline-flex items-center justify-center w-20 h-20 rounded-3xl bg-indigo-600 mb-6 shadow-xl shadow-indigo-200">
              <BookOpen className="text-white" size={40} />
            </div>
            <h1 className="text-3xl font-extrabold text-slate-900 tracking-tight">Goglo Academy</h1>
            <p className="text-slate-500 mt-2">Your bridge to exam success</p>
          </div>

          <form onSubmit={handleLogin} className="space-y-4 bg-white p-8 rounded-3xl shadow-sm border border-slate-100">
            <div className="space-y-1">
              <label className="text-sm font-semibold text-slate-700">Phone Number</label>
              <div className="relative">
                <Phone className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" size={18} />
                <input
                  type="tel"
                  className="w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl focus:ring-2 focus:ring-indigo-500 focus:border-transparent outline-none transition-all"
                  placeholder="0911..."
                  required
                  onChange={(e) => setAuthForm({ ...authForm, phone: e.target.value })}
                />
              </div>
            </div>

            <div className="space-y-1">
              <label className="text-sm font-semibold text-slate-700">Password</label>
              <div className="relative">
                <Lock className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" size={18} />
                <input
                  type="password"
                  className="w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl focus:ring-2 focus:ring-indigo-500 focus:border-transparent outline-none transition-all"
                  placeholder="••••••••"
                  required
                  onChange={(e) => setAuthForm({ ...authForm, password: e.target.value })}
                />
              </div>
            </div>

            <button
              type="submit"
              className="w-full py-4 bg-indigo-600 text-white font-bold rounded-xl shadow-lg shadow-indigo-100 hover:bg-indigo-700 active:scale-[0.98] transition-all"
            >
              Sign In
            </button>
            <p className="text-center text-xs text-slate-400 mt-4">
              By logging in, you agree to our Terms of Service
            </p>
          </form>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-slate-50 pb-24 font-sans select-none">
      {/* Header */}
      <header className="sticky top-0 bg-white border-b border-gray-100 px-5 py-4 flex justify-between items-center z-40">
        <div>
          <h2 className="text-xl font-bold text-slate-800">Goglo Academy</h2>
          <p className="text-xs text-slate-400 font-medium">Hello, {user.name} 👋</p>
        </div>
        <div className="flex gap-2">
          <button 
             onClick={() => setIsOfflineMode(!isOfflineMode)}
             className={`p-2 rounded-full transition-colors ${isOfflineMode ? 'bg-green-100 text-green-600' : 'bg-slate-100 text-slate-400'}`}
          >
            <DownloadCloud size={20} />
          </button>
        </div>
      </header>

      <main className="p-5 max-w-2xl mx-auto">
        {/* Search Bar */}
        <div className="relative mb-6">
          <Search className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" size={18} />
          <input
            type="text"
            placeholder="Search lessons, topics..."
            className="w-full pl-10 pr-4 py-3 bg-white border border-slate-200 rounded-2xl shadow-sm focus:ring-2 focus:ring-indigo-500 outline-none"
            value={searchQuery}
            onChange={(e) => setSearchQuery(e.target.value)}
          />
        </div>

        {view === 'home' && (
          <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
            {/* Quick Stats */}
            <div className="grid grid-cols-2 gap-4">
              <div className="bg-indigo-600 p-4 rounded-3xl text-white shadow-lg shadow-indigo-100">
                <p className="text-xs opacity-80">Course Progress</p>
                <h3 className="text-2xl font-bold mt-1">64%</h3>
                <div className="w-full bg-white/20 h-1.5 mt-3 rounded-full overflow-hidden">
                  <div className="bg-white h-full" style={{ width: '64%' }}></div>
                </div>
              </div>
              <div className="bg-emerald-500 p-4 rounded-3xl text-white shadow-lg shadow-emerald-100">
                <p className="text-xs opacity-80">Mock Exams</p>
                <h3 className="text-2xl font-bold mt-1">12/15</h3>
                <p className="text-[10px] mt-2 bg-white/20 inline-block px-2 py-0.5 rounded-full">Completed</p>
              </div>
            </div>

            {/* Categories */}
            <div>
              <h3 className="font-bold text-slate-800 mb-3 flex justify-between items-center">
                Study Subjects
                <span className="text-xs text-indigo-600 font-semibold">View All</span>
              </h3>
              <div className="flex gap-3 overflow-x-auto pb-2 no-scrollbar">
                {categories.map((cat) => (
                  <button key={cat} className="flex-shrink-0 px-5 py-2 bg-white border border-slate-200 rounded-full text-sm font-medium text-slate-600 hover:border-indigo-500 hover:text-indigo-600 transition-all">
                    {cat}
                  </button>
                ))}
              </div>
            </div>

            {/* Recent Lessons */}
            <div>
              <h3 className="font-bold text-slate-800 mb-4">Continue Learning</h3>
              <div className="space-y-4">
                {lessons.map((lesson) => (
                  <div 
                    key={lesson.id} 
                    onClick={() => { setSelectedItem(lesson); setView('lesson-detail'); }}
                    className="bg-white p-3 rounded-2xl border border-slate-100 flex gap-4 cursor-pointer active:bg-slate-50 transition-colors"
                  >
                    <div className="relative w-24 h-24 flex-shrink-0 rounded-xl overflow-hidden bg-slate-200">
                      <img src={lesson.thumbnail} alt="" className="w-full h-full object-cover" />
                      <div className="absolute inset-0 flex items-center justify-center bg-black/10">
                        <PlayCircle className="text-white drop-shadow-md" size={32} />
                      </div>
                    </div>
                    <div className="flex-grow py-1">
                      <p className="text-[10px] uppercase font-bold text-indigo-500 tracking-wider">{lesson.category}</p>
                      <h4 className="font-bold text-slate-800 leading-tight mt-1">{lesson.title}</h4>
                      <div className="flex items-center gap-3 text-slate-400 mt-2">
                        <span className="text-[11px] flex items-center gap-1"><Clock size={12}/> {lesson.duration}</span>
                        <span className="text-[11px] flex items-center gap-1"><User size={12}/> {lesson.instructor}</span>
                      </div>
                      <ProgressBar value={lesson.progress} />
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {view === 'lessons' && (
          <div className="space-y-4 animate-in fade-in duration-300">
            <h3 className="text-xl font-bold text-slate-800">All Video Lessons</h3>
            {lessons.map((lesson) => (
              <div 
                key={lesson.id}
                onClick={() => { setSelectedItem(lesson); setView('lesson-detail'); }}
                className="group relative overflow-hidden rounded-2xl aspect-video bg-slate-900 mb-4 cursor-pointer"
              >
                <img src={lesson.thumbnail} className="absolute inset-0 w-full h-full object-cover opacity-60 group-hover:scale-105 transition-transform duration-500" alt="" />
                <div className="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent p-5 flex flex-col justify-end">
                   <h4 className="text-white font-bold text-lg">{lesson.title}</h4>
                   <p className="text-white/70 text-sm">{lesson.instructor} • {lesson.duration}</p>
                </div>
                <div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-white/20 backdrop-blur-md p-4 rounded-full">
                  <PlayCircle className="text-white" size={40} />
                </div>
              </div>
            ))}
          </div>
        )}

        {view === 'pdfs' && (
          <div className="space-y-4 animate-in fade-in duration-300">
            <h3 className="text-xl font-bold text-slate-800">Study Materials</h3>
            <div className="grid grid-cols-1 gap-3">
              {pdfs.map((pdf) => (
                <div key={pdf.id} className="bg-white p-4 rounded-2xl border border-slate-100 flex items-center justify-between group">
                  <div className="flex items-center gap-4">
                    <div className="w-12 h-12 bg-red-50 text-red-500 rounded-xl flex items-center justify-center">
                      <FileText size={24} />
                    </div>
                    <div>
                      <h4 className="font-bold text-slate-800 text-sm">{pdf.title}</h4>
                      <p className="text-xs text-slate-400">{pdf.category} • {pdf.size}</p>
                    </div>
                  </div>
                  <button className="p-2 text-slate-400 hover:text-indigo-600 hover:bg-indigo-50 rounded-lg transition-all">
                    <Download size={20} />
                  </button>
                </div>
              ))}
            </div>
          </div>
        )}

        {view === 'lesson-detail' && selectedItem && (
          <div className="animate-in slide-in-from-right-4 duration-300">
            <button onClick={() => setView('home')} className="flex items-center gap-2 text-slate-500 mb-6 font-medium">
              <ArrowLeft size={18} /> Back to Dashboard
            </button>
            <div className="aspect-video bg-black rounded-2xl overflow-hidden shadow-2xl relative mb-6">
              <img src={selectedItem.thumbnail} className="w-full h-full object-cover opacity-50" alt="" />
              <div className="absolute inset-0 flex flex-col items-center justify-center text-white p-6 text-center">
                <PlayCircle size={64} className="mb-4" />
                <h4 className="text-lg font-bold">Resuming Lesson...</h4>
                <p className="text-sm opacity-80">You stopped at 12:45</p>
              </div>
            </div>
            <h3 className="text-2xl font-bold text-slate-800">{selectedItem.title}</h3>
            <div className="flex items-center gap-4 mt-4 py-4 border-y border-slate-100">
              <div className="w-10 h-10 bg-indigo-100 rounded-full flex items-center justify-center text-indigo-600 font-bold uppercase">
                {selectedItem.instructor.charAt(selectedItem.instructor.indexOf(' ') + 1)}
              </div>
              <div>
                <p className="text-sm font-bold text-slate-800">{selectedItem.instructor}</p>
                <p className="text-xs text-slate-500">Curriculum Expert</p>
              </div>
            </div>
            <div className="mt-6">
              <h4 className="font-bold text-slate-800 mb-3">Lesson Description</h4>
              <p className="text-sm text-slate-600 leading-relaxed">
                This comprehensive session covers all the critical concepts required for the entrance exam. 
                We dive deep into principles, practice multiple examples, and look at previous exam trends.
              </p>
            </div>
            <button className="w-full mt-8 py-4 bg-indigo-600 text-white rounded-2xl font-bold shadow-lg shadow-indigo-100">
              Take Practice Quiz
            </button>
          </div>
        )}

        {view === 'profile' && (
          <div className="animate-in fade-in duration-300 space-y-6">
            <div className="text-center py-6">
              <div className="w-24 h-24 bg-indigo-600 text-white rounded-full mx-auto flex items-center justify-center text-3xl font-bold border-4 border-white shadow-xl mb-4">
                {user.name.charAt(0)}
              </div>
              <h3 className="text-xl font-bold text-slate-800">{user.name}</h3>
              <p className="text-sm text-slate-400">{user.phone}</p>
            </div>

            <div className="bg-white rounded-3xl overflow-hidden border border-slate-100 shadow-sm">
              {[
                { label: 'My Downloads', icon: Download, color: 'text-blue-500' },
                { label: 'Exam Certificates', icon: CheckCircle, color: 'text-emerald-500' },
                { label: 'Account Settings', icon: User, color: 'text-slate-500' },
                { label: 'Logout', icon: LogOut, color: 'text-red-500', action: () => setUser(null) },
              ].map((item, idx) => (
                <button 
                  key={idx}
                  onClick={item.action}
                  className="w-full p-4 flex items-center justify-between border-b border-slate-50 last:border-0 active:bg-slate-50"
                >
                  <div className="flex items-center gap-3">
                    <div className={`${item.color} p-2 rounded-lg bg-opacity-10 bg-current`}>
                      <item.icon size={20} />
                    </div>
                    <span className="font-medium text-slate-700">{item.label}</span>
                  </div>
                  <ChevronRight size={18} className="text-slate-300" />
                </button>
              ))}
            </div>
            
            <div className="p-4 bg-indigo-50 rounded-2xl flex items-center justify-between">
              <div>
                <p className="text-sm font-bold text-indigo-900">Subscription Status</p>
                <p className="text-xs text-indigo-600">Premium Plan (Active)</p>
              </div>
              <span className="bg-indigo-600 text-white text-[10px] px-2 py-1 rounded-md font-bold uppercase">Pro</span>
            </div>
          </div>
        )}
      </main>

      {/* Navigation */}
      <BottomNav />

      {/* Offline Mode Toast Overlay */}
      {isOfflineMode && (
        <div className="fixed top-20 left-1/2 -translate-x-1/2 bg-green-600 text-white px-4 py-2 rounded-full text-xs font-bold shadow-lg animate-bounce z-50">
          Viewing Offline Content
        </div>
      )}
    </div>
  );
};

export default App;

```
