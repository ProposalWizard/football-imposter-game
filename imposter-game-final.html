import React, { useState, useEffect } from 'react';
import { Users, Eye, EyeOff, RefreshCw, UserX, Trophy, Shield, Lock, Settings, Tag, Upload, Plus, X, Edit2, Trash2 } from 'lucide-react';

export default function ImposterGame() {
  const [gameState, setGameState] = useState('setup'); // setup, playing, admin, join-room
  const [players, setPlayers] = useState(['']);
  const [footballers, setFootballers] = useState([]);
  const [assignments, setAssignments] = useState([]);
  const [imposterIndex, setImposterIndex] = useState(null);
  const [revealedPlayer, setRevealedPlayer] = useState(null);
  const [showAllRoles, setShowAllRoles] = useState(false);
  const [selectedGameMode, setSelectedGameMode] = useState([]);
  const [gameType, setGameType] = useState(null); // 'local' or 'room'
  const [roomCode, setRoomCode] = useState('');
  const [roomCodeInput, setRoomCodeInput] = useState('');
  const [playerNameInput, setPlayerNameInput] = useState('');
  const [currentPlayerRole, setCurrentPlayerRole] = useState(null);
  
  // Admin state
  const [isAdmin, setIsAdmin] = useState(false);
  const [passwordInput, setPasswordInput] = useState('');
  const [showPasswordPrompt, setShowPasswordPrompt] = useState(false);
  const [editingPlayer, setEditingPlayer] = useState(null);
  const [newPlayerName, setNewPlayerName] = useState('');
  const [newPlayerTags, setNewPlayerTags] = useState([]);
  const [bulkImportText, setBulkImportText] = useState('');
  const [showBulkImport, setShowBulkImport] = useState(false);
  const [searchQuery, setSearchQuery] = useState('');
  const [categoryFilter, setCategoryFilter] = useState('all');
  const [isNotFilter, setIsNotFilter] = useState(false);
  const [quickAssignMode, setQuickAssignMode] = useState(null); // null or category name

  const ADMIN_PASSWORD = 'PANEL';
  
  // Fixed categories - organized into logical groups
  const CATEGORIES = {
    Position: ['Strikers', 'Wingers', 'Midfielders', 'Defenders', 'Goalkeepers'],
    Nation: ['European', 'South American', 'African'],
    Leagues: ['Current Premier League', 'Plays in the Champions League'],
    Age: ['Under 21']
  };
  
  // Flat list for filtering
  const ALL_CATEGORIES = [...CATEGORIES.Position, ...CATEGORIES.Nation, ...CATEGORIES.Leagues, ...CATEGORIES.Age];

  // Load data from storage on mount
  useEffect(() => {
    loadData();
  }, []);

  const loadData = async () => {
    try {
      const result = await window.storage.get('footballer-database-v3');
      if (result && result.value) {
        const data = JSON.parse(result.value);
        setFootballers(data.footballers || []);
      } else {
        // Initialize with example data
        const exampleData = [
          { name: 'Lionel Messi', tags: [] },
          { name: 'Cristiano Ronaldo', tags: [] },
          { name: 'Erling Haaland', tags: [] },
        ];
        await saveData(exampleData);
      }
    } catch (error) {
      console.log('Error loading data:', error);
    }
  };

  const saveData = async (footballerList) => {
    try {
      const data = {
        footballers: footballerList
      };
      await window.storage.set('footballer-database-v3', JSON.stringify(data));
      setFootballers(footballerList);
    } catch (error) {
      console.error('Failed to save data:', error);
    }
  };

  const handleAdminLogin = () => {
    if (passwordInput === ADMIN_PASSWORD) {
      setIsAdmin(true);
      setGameState('admin');
      setShowPasswordPrompt(false);
      setPasswordInput('');
    } else {
      alert('Incorrect password!');
      setPasswordInput('');
    }
  };

  const addPlayer = () => {
    setPlayers([...players, '']);
  };

  const updatePlayer = (index, value) => {
    const newPlayers = [...players];
    newPlayers[index] = value;
    setPlayers(newPlayers);
  };

  const removePlayer = (index) => {
    const newPlayers = players.filter((_, i) => i !== index);
    setPlayers(newPlayers.length === 0 ? [''] : newPlayers);
  };

  const getFilteredFootballers = () => {
    if (selectedGameMode.length === 0) {
      // No filters selected - return all players
      return footballers;
    }
    
    // Return players that have ALL selected categories (AND logic)
    return footballers.filter(f => 
      selectedGameMode.every(category => f.tags.includes(category))
    );
  };

  const toggleGameMode = (category) => {
    if (selectedGameMode.includes(category)) {
      // Remove category
      setSelectedGameMode(selectedGameMode.filter(c => c !== category));
    } else {
      // Add category
      setSelectedGameMode([...selectedGameMode, category]);
    }
  };

  const clearGameModes = () => {
    setSelectedGameMode([]);
  };

  const generateRoomCode = () => {
    const words = ['BOLT', 'KICK', 'GOAL', 'PASS', 'SHOT', 'TEAM', 'PLAY', 'BOOT', 'BALL', 'STAR'];
    const word = words[Math.floor(Math.random() * words.length)];
    const num = Math.floor(1000 + Math.random() * 9000);
    return `${word}-${num}`;
  };

  const startGame = async () => {
    const validPlayers = players.filter(p => p.trim() !== '');
    
    if (validPlayers.length < 3) {
      alert('You need at least 3 players to start the game!');
      return;
    }

    const filtered = getFilteredFootballers();
    
    if (filtered.length < 1) {
      alert('No footballers available for this game mode!');
      return;
    }

    // Pick random imposter
    const imposter = Math.floor(Math.random() * validPlayers.length);
    setImposterIndex(imposter);

    // Pick one random footballer for innocent players
    const randomIndex = Math.floor(Math.random() * filtered.length);
    const innocentPlayer = filtered[randomIndex].name;

    // Assign roles
    const newAssignments = validPlayers.map((name, index) => ({
      name,
      footballer: index === imposter ? null : innocentPlayer,
      isImposter: index === imposter
    }));

    setAssignments(newAssignments);

    if (gameType === 'room') {
      // Generate room code and save to storage
      const code = generateRoomCode();
      setRoomCode(code);
      
      try {
        const roomData = {
          code,
          assignments: newAssignments,
          gameMode: selectedGameMode,
          timestamp: Date.now()
        };
        await window.storage.set(`room-${code}`, JSON.stringify(roomData), true); // shared storage
        setGameState('playing');
      } catch (error) {
        console.error('Failed to create room:', error);
        alert('Failed to create room. Please try again.');
      }
    } else {
      // Local game
      setGameState('playing');
    }
    
    setRevealedPlayer(null);
  };

  const resetGame = () => {
    setGameState('setup');
    setAssignments([]);
    setImposterIndex(null);
    setRevealedPlayer(null);
    setShowAllRoles(false);
    setSelectedGameMode([]);
    setGameType(null);
    setRoomCode('');
    setCurrentPlayerRole(null);
  };

  const joinRoom = async () => {
    if (!roomCodeInput.trim()) {
      alert('Please enter a room code');
      return;
    }

    if (!playerNameInput.trim()) {
      alert('Please enter your name');
      return;
    }

    try {
      const result = await window.storage.get(`room-${roomCodeInput.toUpperCase()}`, true);
      
      if (!result || !result.value) {
        alert('Room not found. Please check the code and try again.');
        return;
      }

      const roomData = JSON.parse(result.value);
      
      // Find this player's assignment
      const playerAssignment = roomData.assignments.find(
        a => a.name.toLowerCase() === playerNameInput.trim().toLowerCase()
      );

      if (!playerAssignment) {
        alert(`Player "${playerNameInput}" not found in this game. Check your name with the host.`);
        return;
      }

      setCurrentPlayerRole(playerAssignment);
      setGameState('playing');
      setGameType('room');
      setRoomCode(roomCodeInput.toUpperCase());
    } catch (error) {
      console.error('Failed to join room:', error);
      alert('Failed to join room. Please try again.');
    }
  };

  const revealRole = (index) => {
    setRevealedPlayer(index);
    setTimeout(() => setRevealedPlayer(null), 5000);
  };

  // Admin functions
  const saveNewPlayer = () => {
    if (!newPlayerName.trim()) {
      alert('Please enter a player name');
      return;
    }

    const newFootballer = {
      name: newPlayerName.trim(),
      tags: newPlayerTags
    };

    const updatedFootballers = [...footballers, newFootballer];
    
    saveData(updatedFootballers);
    setNewPlayerName('');
    setNewPlayerTags([]);
  };

  const deleteFootballer = (footballerToDelete) => {
    // Clear editing state first
    setEditingPlayer(null);
    setNewPlayerName('');
    setNewPlayerTags([]);
    
    // Filter out the player
    const updatedFootballers = footballers.filter(f => f.name !== footballerToDelete.name);
    
    // Save immediately
    setFootballers(updatedFootballers);
    
    // Also save to storage
    try {
      const data = {
        footballers: updatedFootballers
      };
      window.storage.set('footballer-database-v3', JSON.stringify(data));
    } catch (error) {
      console.error('Failed to save after delete:', error);
    }
  };

  const startEditPlayer = (footballer, index) => {
    setEditingPlayer(index);
    setNewPlayerName(footballer.name);
    setNewPlayerTags(footballer.tags);
  };

  const saveEditedPlayer = () => {
    if (!newPlayerName.trim()) {
      alert('Please enter a player name');
      return;
    }

    const updatedFootballers = [...footballers];
    updatedFootballers[editingPlayer] = {
      name: newPlayerName.trim(),
      tags: newPlayerTags
    };
    
    saveData(updatedFootballers);
    setEditingPlayer(null);
    setNewPlayerName('');
    setNewPlayerTags([]);
  };

  const cancelEdit = () => {
    setEditingPlayer(null);
    setNewPlayerName('');
    setNewPlayerTags([]);
  };

  const toggleTag = (tag) => {
    if (newPlayerTags.includes(tag)) {
      setNewPlayerTags(newPlayerTags.filter(t => t !== tag));
    } else {
      setNewPlayerTags([...newPlayerTags, tag]);
    }
  };

  const processBulkImport = () => {
    if (!bulkImportText.trim()) {
      alert('Please paste your player list');
      return;
    }

    const lines = bulkImportText.trim().split('\n');
    const newFootballers = [];

    for (const line of lines) {
      const name = line.trim();
      if (name) {
        newFootballers.push({ name, tags: [] }); // All start with no categories
      }
    }

    if (newFootballers.length === 0) {
      alert('No valid players found');
      return;
    }

    const updatedFootballers = [...footballers, ...newFootballers];

    saveData(updatedFootballers);
    setBulkImportText('');
    setShowBulkImport(false);
    alert(`Successfully imported ${newFootballers.length} players! Now assign them to categories.`);
  };

  // Get newly added players (no categories assigned)
  const getNewlyAddedPlayers = () => {
    return footballers.filter(f => f.tags.length === 0);
  };

  // Get filtered players based on search and category
  const getFilteredPlayers = () => {
    let filtered = footballers;

    // Filter by search query
    if (searchQuery.trim()) {
      filtered = filtered.filter(f => 
        f.name.toLowerCase().includes(searchQuery.toLowerCase())
      );
    }

    // Filter by category
    if (categoryFilter !== 'all') {
      if (categoryFilter === 'uncategorized') {
        filtered = filtered.filter(f => f.tags.length === 0);
      } else {
        if (isNotFilter) {
          // NOT filter - show players that DON'T have this category
          filtered = filtered.filter(f => !f.tags.includes(categoryFilter));
        } else {
          // Normal filter - show players that DO have this category
          filtered = filtered.filter(f => f.tags.includes(categoryFilter));
        }
      }
    }

    return filtered;
  };

  // Export all players to text file
  const exportPlayers = () => {
    let exportText = 'FOOTBALL IMPOSTER GAME - PLAYER DATABASE\n';
    exportText += '==========================================\n\n';
    
    footballers.forEach(footballer => {
      exportText += `${footballer.name}\n`;
      if (footballer.tags.length > 0) {
        exportText += `Categories: ${footballer.tags.join(', ')}\n`;
      } else {
        exportText += `Categories: None assigned\n`;
      }
      exportText += '\n';
    });

    // Create download
    const blob = new Blob([exportText], { type: 'text/plain' });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = 'imposter-game-players.txt';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
  };

  // Quick assign - toggle a category for a player
  const quickAssignToggle = (footballer) => {
    if (!quickAssignMode) return;
    
    const footballerIndex = footballers.findIndex(f => f.name === footballer.name);
    if (footballerIndex === -1) return;
    
    const updatedFootballers = [...footballers];
    const player = updatedFootballers[footballerIndex];
    
    if (player.tags.includes(quickAssignMode)) {
      // Remove category
      player.tags = player.tags.filter(t => t !== quickAssignMode);
    } else {
      // Add category
      player.tags = [...player.tags, quickAssignMode];
    }
    
    // Save immediately
    setFootballers(updatedFootballers);
    
    try {
      const data = { footballers: updatedFootballers };
      window.storage.set('footballer-database-v3', JSON.stringify(data));
    } catch (error) {
      console.error('Failed to save:', error);
    }
  };

  // ADMIN PANEL
  if (gameState === 'admin') {
    return (
      <div className="min-h-screen bg-gradient-to-br from-slate-950 via-blue-950 to-slate-950 p-4 md:p-8 font-['Space_Mono',monospace]">
        <div className="max-w-6xl mx-auto">
          {/* Header */}
          <div className="flex items-center justify-between mb-8">
            <div className="flex items-center gap-3">
              <Settings className="text-cyan-400" size={32} />
              <h1 className="text-4xl md:text-5xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-300 tracking-tighter">
                ADMIN PANEL
              </h1>
            </div>
            <button
              onClick={() => { setGameState('setup'); setIsAdmin(false); }}
              className="bg-slate-700/50 hover:bg-slate-700/70 text-cyan-300 px-6 py-3 rounded-lg border-2 border-cyan-500/30 font-bold transition-all"
            >
              EXIT ADMIN
            </button>
          </div>

          {/* Bulk Import Section */}
          <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-6 border-2 border-cyan-500/30 shadow-2xl mb-6">
            <button
              onClick={() => setShowBulkImport(!showBulkImport)}
              className="flex items-center gap-3 text-2xl font-black text-cyan-300 tracking-tight mb-4"
            >
              <Upload size={28} />
              BULK IMPORT PLAYERS
            </button>
            
            {showBulkImport && (
              <div>
                <div className="bg-slate-900/50 p-4 rounded-lg mb-4 border border-cyan-500/20">
                  <p className="text-cyan-300 mb-2 font-bold">FORMAT:</p>
                  <code className="text-cyan-400 text-sm block mb-2">
                    Just paste player names, one per line
                  </code>
                  <p className="text-cyan-300/70 text-sm mb-2">EXAMPLE:</p>
                  <code className="text-cyan-400/70 text-xs block">
                    Lionel Messi<br/>
                    Cristiano Ronaldo<br/>
                    Peter Schmeichel<br/>
                    Erling Haaland
                  </code>
                  <p className="text-cyan-300/70 text-xs mt-3">
                    All players will be imported with NO categories selected. You'll assign categories after import.
                  </p>
                </div>
                
                <textarea
                  value={bulkImportText}
                  onChange={(e) => setBulkImportText(e.target.value)}
                  placeholder="Paste your player list here..."
                  className="w-full h-64 bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono text-sm mb-4"
                />
                
                <div className="flex gap-3">
                  <button
                    onClick={processBulkImport}
                    className="bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 px-6 py-3 rounded-lg border-2 border-cyan-500/40 font-bold transition-all"
                  >
                    IMPORT
                  </button>
                  <button
                    onClick={() => { setBulkImportText(''); setShowBulkImport(false); }}
                    className="bg-slate-700/50 hover:bg-slate-700/70 text-slate-300 px-6 py-3 rounded-lg border-2 border-slate-500/30 font-bold transition-all"
                  >
                    CANCEL
                  </button>
                </div>
              </div>
            )}
          </div>

          {/* Add/Edit Player Form */}
          <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-6 border-2 border-cyan-500/30 shadow-2xl mb-6">
            <h2 className="text-2xl font-black text-cyan-300 tracking-tight mb-4">
              {editingPlayer !== null ? 'EDIT PLAYER' : 'ADD NEW PLAYER'}
            </h2>
            
            <input
              type="text"
              value={newPlayerName}
              onChange={(e) => setNewPlayerName(e.target.value)}
              placeholder="Player name..."
              className="w-full bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono mb-4"
            />

            <div className="mb-4">
              <div className="mb-4">
                <span className="text-cyan-300 font-bold">SELECT CATEGORIES:</span>
              </div>
              
              {/* Position Row */}
              <div className="mb-4">
                <div className="text-cyan-400 text-sm font-bold mb-2">POSITION:</div>
                <div className="flex flex-wrap gap-2">
                  {CATEGORIES.Position.map((category) => (
                    <button
                      key={category}
                      onClick={() => toggleTag(category)}
                      className={`px-4 py-3 rounded-lg font-bold transition-all border-2 text-sm ${
                        newPlayerTags.includes(category)
                          ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                          : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                      }`}
                    >
                      {newPlayerTags.includes(category) ? '✓ ' : ''}{category}
                    </button>
                  ))}
                </div>
              </div>

              {/* Nation Row */}
              <div className="mb-4">
                <div className="text-cyan-400 text-sm font-bold mb-2">NATION:</div>
                <div className="flex flex-wrap gap-2">
                  {CATEGORIES.Nation.map((category) => (
                    <button
                      key={category}
                      onClick={() => toggleTag(category)}
                      className={`px-4 py-3 rounded-lg font-bold transition-all border-2 text-sm ${
                        newPlayerTags.includes(category)
                          ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                          : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                      }`}
                    >
                      {newPlayerTags.includes(category) ? '✓ ' : ''}{category}
                    </button>
                  ))}
                </div>
              </div>

              {/* Leagues Row */}
              <div className="mb-4">
                <div className="text-cyan-400 text-sm font-bold mb-2">LEAGUES:</div>
                <div className="flex flex-wrap gap-2">
                  {CATEGORIES.Leagues.map((category) => (
                    <button
                      key={category}
                      onClick={() => toggleTag(category)}
                      className={`px-4 py-3 rounded-lg font-bold transition-all border-2 text-sm ${
                        newPlayerTags.includes(category)
                          ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                          : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                      }`}
                    >
                      {newPlayerTags.includes(category) ? '✓ ' : ''}{category}
                    </button>
                  ))}
                </div>
              </div>

              {/* Age Row */}
              <div className="mb-4">
                <div className="text-cyan-400 text-sm font-bold mb-2">AGE:</div>
                <div className="flex flex-wrap gap-2">
                  {CATEGORIES.Age.map((category) => (
                    <button
                      key={category}
                      onClick={() => toggleTag(category)}
                      className={`px-4 py-3 rounded-lg font-bold transition-all border-2 text-sm ${
                        newPlayerTags.includes(category)
                          ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                          : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                      }`}
                    >
                      {newPlayerTags.includes(category) ? '✓ ' : ''}{category}
                    </button>
                  ))}
                </div>
              </div>
            </div>

            <div className="flex gap-3">
              {editingPlayer !== null ? (
                <>
                  <button
                    onClick={saveEditedPlayer}
                    className="bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 px-6 py-3 rounded-lg border-2 border-cyan-500/40 font-bold transition-all"
                  >
                    SAVE CHANGES
                  </button>
                  <button
                    onClick={cancelEdit}
                    className="bg-slate-700/50 hover:bg-slate-700/70 text-slate-300 px-6 py-3 rounded-lg border-2 border-slate-500/30 font-bold transition-all"
                  >
                    CANCEL
                  </button>
                </>
              ) : (
                <button
                  onClick={saveNewPlayer}
                  className="bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 px-6 py-3 rounded-lg border-2 border-cyan-500/40 font-bold transition-all"
                >
                  ADD PLAYER
                </button>
              )}
            </div>
          </div>

          {/* Newly Added Players Section */}
          {getNewlyAddedPlayers().length > 0 && (
            <div className="bg-amber-900/20 backdrop-blur-xl rounded-2xl p-6 border-2 border-amber-500/40 shadow-2xl mb-6">
              <h2 className="text-2xl font-black text-amber-300 tracking-tight mb-4 flex items-center gap-2">
                <Trophy className="text-amber-400" size={28} />
                NEWLY ADDED PLAYERS ({getNewlyAddedPlayers().length})
              </h2>
              <p className="text-amber-300/70 text-sm mb-4 font-mono">
                These players need categories assigned. Click edit to add them.
              </p>
              
              <div className="space-y-2 max-h-80 overflow-y-auto">
                {getNewlyAddedPlayers().map((footballer, index) => {
                  return (
                    <div key={index} className="bg-slate-700/40 p-4 rounded-lg border border-amber-500/30 flex items-start justify-between hover:bg-slate-700/60 transition-all">
                      <div className="flex-1">
                        <div className="text-white font-bold mb-2">{footballer.name}</div>
                        <span className="bg-slate-600/30 text-slate-400 px-2 py-1 rounded text-xs border border-slate-500/30 italic">
                          No categories assigned
                        </span>
                      </div>
                      <div className="flex gap-2 ml-4">
                        <button
                          onClick={() => {
                            const actualIndex = footballers.findIndex(f => f.name === footballer.name);
                            startEditPlayer(footballer, actualIndex);
                          }}
                          className="text-amber-400 hover:text-amber-300 transition-all p-2 hover:bg-amber-500/10 rounded font-bold"
                          title="Assign categories"
                        >
                          <Edit2 size={18} />
                        </button>
                        <button
                          onClick={() => deleteFootballer(footballer)}
                          className="text-red-400 hover:text-red-300 transition-all p-2 hover:bg-red-500/10 rounded"
                          title="Delete player"
                        >
                          <Trash2 size={18} />
                        </button>
                      </div>
                    </div>
                  );
                })}
              </div>
            </div>
          )}

          {/* Player List */}
          <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-6 border-2 border-cyan-500/30 shadow-2xl">
            <div className="flex items-center justify-between mb-4">
              <h2 className="text-2xl font-black text-cyan-300 tracking-tight">
                ALL PLAYERS ({footballers.length})
              </h2>
              <button
                onClick={exportPlayers}
                className="bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 px-4 py-2 rounded-lg border-2 border-cyan-500/40 font-bold transition-all text-sm flex items-center gap-2"
              >
                <Upload size={16} />
                EXPORT LIST
              </button>
            </div>

            {/* Quick Assign Mode */}
            <div className="mb-4 p-4 bg-amber-900/20 rounded-lg border-2 border-amber-500/40">
              <div className="text-amber-300 font-bold mb-3 text-lg">⚡ QUICK ASSIGN MODE</div>
              <p className="text-amber-300/70 text-sm mb-3 font-mono">
                Select a category, then click players below to quickly add/remove them from that category
              </p>
              
              <div className="flex flex-wrap gap-2 mb-3">
                {ALL_CATEGORIES.map((category) => (
                  <button
                    key={category}
                    onClick={() => setQuickAssignMode(quickAssignMode === category ? null : category)}
                    className={`px-4 py-2 rounded-lg font-bold transition-all border-2 text-sm ${
                      quickAssignMode === category
                        ? 'bg-amber-500/40 border-amber-400 text-amber-200'
                        : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                    }`}
                  >
                    {quickAssignMode === category ? '⚡ ' : ''}{category}
                  </button>
                ))}
              </div>

              {quickAssignMode && (
                <div className="bg-amber-500/10 p-3 rounded border border-amber-500/30">
                  <div className="text-amber-300 font-bold text-sm">
                    ⚡ ACTIVE: {quickAssignMode}
                  </div>
                  <div className="text-amber-300/70 text-xs mt-1">
                    Click any player below to toggle this category on/off
                  </div>
                  <button
                    onClick={() => setQuickAssignMode(null)}
                    className="mt-2 bg-red-500/20 hover:bg-red-500/30 text-red-300 px-3 py-1 rounded text-xs font-bold border border-red-500/30"
                  >
                    EXIT QUICK ASSIGN
                  </button>
                </div>
              )}
            </div>

            {/* Search and Filter */}
            <div className="mb-4 space-y-3">
              <input
                type="text"
                value={searchQuery}
                onChange={(e) => setSearchQuery(e.target.value)}
                placeholder="Search players..."
                className="w-full bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono"
              />
              
              {/* NOT Toggle Button */}
              <div className="flex items-center gap-3">
                <button
                  onClick={() => {
                    setIsNotFilter(!isNotFilter);
                    // Reset to 'all' if turning NOT off
                    if (!isNotFilter && categoryFilter === 'all') {
                      // Keep as is
                    }
                  }}
                  className={`px-4 py-2 rounded-lg font-bold transition-all border-2 text-sm ${
                    isNotFilter
                      ? 'bg-red-500/30 border-red-400 text-red-300'
                      : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                  }`}
                >
                  {isNotFilter ? '✓ NOT MODE' : 'NOT'}
                </button>
                {isNotFilter && categoryFilter !== 'all' && categoryFilter !== 'uncategorized' && (
                  <span className="text-red-300 text-sm font-mono">
                    Showing players WITHOUT: {categoryFilter}
                  </span>
                )}
              </div>
              
              <div className="flex flex-wrap gap-2">
                <button
                  onClick={() => { setCategoryFilter('all'); setIsNotFilter(false); }}
                  className={`px-4 py-2 rounded-lg font-bold transition-all border-2 text-sm ${
                    categoryFilter === 'all'
                      ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                      : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                  }`}
                >
                  All
                </button>
                <button
                  onClick={() => { setCategoryFilter('uncategorized'); setIsNotFilter(false); }}
                  className={`px-4 py-2 rounded-lg font-bold transition-all border-2 text-sm ${
                    categoryFilter === 'uncategorized'
                      ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                      : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                  }`}
                >
                  Uncategorized
                </button>
                {ALL_CATEGORIES.map((category) => (
                  <button
                    key={category}
                    onClick={() => setCategoryFilter(category)}
                    className={`px-4 py-2 rounded-lg font-bold transition-all border-2 text-sm ${
                      categoryFilter === category
                        ? isNotFilter
                          ? 'bg-red-500/30 border-red-400 text-red-300'
                          : 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                        : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                    }`}
                  >
                    {category}
                  </button>
                ))}
              </div>
            </div>
            
            <div className="space-y-2 max-h-96 overflow-y-auto">
              {getFilteredPlayers().map((footballer, index) => {
                const actualIndex = footballers.findIndex(f => f.name === footballer.name);
                const hasQuickAssignCategory = quickAssignMode && footballer.tags.includes(quickAssignMode);
                
                return (
                  <div 
                    key={index} 
                    onClick={() => quickAssignMode && quickAssignToggle(footballer)}
                    className={`p-4 rounded-lg border flex items-start justify-between transition-all ${
                      quickAssignMode 
                        ? hasQuickAssignCategory
                          ? 'bg-amber-500/20 border-amber-500/40 cursor-pointer hover:bg-amber-500/30'
                          : 'bg-slate-700/30 border-cyan-500/10 cursor-pointer hover:bg-slate-700/50'
                        : 'bg-slate-700/30 border-cyan-500/10 hover:bg-slate-700/40'
                    }`}
                  >
                    <div className="flex-1">
                      <div className="flex items-center gap-2">
                        <div className="text-white font-bold">{footballer.name}</div>
                        {quickAssignMode && hasQuickAssignCategory && (
                          <span className="text-amber-400 text-lg">⚡</span>
                        )}
                      </div>
                      <div className="flex flex-wrap gap-1 mt-2">
                        {footballer.tags.length === 0 ? (
                          <span className="bg-slate-600/30 text-slate-400 px-2 py-1 rounded text-xs border border-slate-500/30 italic">
                            No categories assigned
                          </span>
                        ) : (
                          footballer.tags.map((tag) => (
                            <span 
                              key={tag} 
                              className={`px-2 py-1 rounded text-xs border ${
                                quickAssignMode && tag === quickAssignMode
                                  ? 'bg-amber-500/30 text-amber-300 border-amber-500/50 font-bold'
                                  : 'bg-cyan-500/20 text-cyan-300 border-cyan-500/30'
                              }`}
                            >
                              {tag}
                            </span>
                          ))
                        )}
                      </div>
                    </div>
                    {!quickAssignMode && (
                      <div className="flex gap-2 ml-4">
                        <button
                          onClick={() => startEditPlayer(footballer, actualIndex)}
                          className="text-blue-400 hover:text-blue-300 transition-all p-2 hover:bg-blue-500/10 rounded"
                          title="Edit categories"
                        >
                          <Edit2 size={18} />
                        </button>
                        <button
                          onClick={() => deleteFootballer(footballer)}
                          className="text-red-400 hover:text-red-300 transition-all p-2 hover:bg-red-500/10 rounded"
                          title="Delete player"
                        >
                          <Trash2 size={18} />
                        </button>
                      </div>
                    )}
                  </div>
                );
              })}
              {getFilteredPlayers().length === 0 && (
                <div className="text-center py-8 text-slate-500 font-mono">
                  {searchQuery || categoryFilter !== 'all' 
                    ? 'No players found matching your filters'
                    : 'No players yet. Add some above or use bulk import!'}
                </div>
              )}
            </div>
          </div>
        </div>
      </div>
    );
  }

  // PASSWORD PROMPT
  if (showPasswordPrompt && !isAdmin) {
    return (
      <div className="min-h-screen bg-gradient-to-br from-blue-950 via-slate-900 to-blue-950 p-4 flex items-center justify-center font-['Space_Mono',monospace]">
        <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-8 border-2 border-cyan-500/30 shadow-2xl max-w-md w-full">
          <div className="flex items-center gap-3 mb-6">
            <Lock className="text-cyan-400" size={32} />
            <h2 className="text-3xl font-black text-cyan-300 tracking-tight">ADMIN LOGIN</h2>
          </div>
          
          <input
            type="password"
            value={passwordInput}
            onChange={(e) => setPasswordInput(e.target.value)}
            onKeyPress={(e) => e.key === 'Enter' && handleAdminLogin()}
            placeholder="Enter password..."
            className="w-full bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono mb-4"
            autoFocus
          />
          
          <div className="flex gap-3">
            <button
              onClick={handleAdminLogin}
              className="flex-1 bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 py-3 rounded-lg border-2 border-cyan-500/40 font-bold transition-all"
            >
              LOGIN
            </button>
            <button
              onClick={() => { setShowPasswordPrompt(false); setPasswordInput(''); }}
              className="flex-1 bg-slate-700/50 hover:bg-slate-700/70 text-slate-300 py-3 rounded-lg border-2 border-slate-500/30 font-bold transition-all"
            >
              CANCEL
            </button>
          </div>
        </div>
      </div>
    );
  }

  // SETUP SCREEN
  if (gameState === 'setup') {
    // If no game type selected, show choice screen
    if (!gameType) {
      return (
        <div className="min-h-screen bg-gradient-to-br from-blue-950 via-slate-900 to-indigo-950 p-4 md:p-8 font-['Space_Mono',monospace] flex items-center justify-center">
          <div className="max-w-4xl w-full">
            {/* Header */}
            <div className="text-center mb-12 relative">
              <div className="absolute inset-0 bg-cyan-500/10 blur-3xl"></div>
              <div className="relative">
                <h1 className="text-6xl md:text-8xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-blue-400 to-indigo-400 mb-4 tracking-tighter transform -skew-y-1">
                  IMPOSTER
                </h1>
                <div className="text-xl md:text-2xl text-cyan-300 font-bold tracking-widest">
                  ⚽ FOOTBALL EDITION ⚽
                </div>
              </div>
              
              {/* Admin Button */}
              <button
                onClick={() => setShowPasswordPrompt(true)}
                className="absolute top-0 right-0 text-cyan-400/50 hover:text-cyan-400 transition-all"
                title="Admin Panel"
              >
                <Settings size={24} />
              </button>
            </div>

            {/* Game Type Selection */}
            <div className="grid md:grid-cols-2 gap-6">
              {/* Host Game */}
              <button
                onClick={() => setGameType('local')}
                className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-8 border-2 border-cyan-500/30 hover:border-cyan-400/50 shadow-2xl transition-all transform hover:scale-105 text-left group"
              >
                <div className="text-4xl mb-4">🖥️</div>
                <h2 className="text-3xl font-black text-cyan-300 mb-3 tracking-tight">LOCAL MODE</h2>
                <p className="text-cyan-200/70 text-sm leading-relaxed font-mono">
                  Everyone gathers around one device. Click names to reveal roles privately.
                </p>
                <div className="mt-4 text-cyan-400 font-bold text-sm">→ Traditional mode</div>
              </button>

              {/* Room Code Game */}
              <button
                onClick={() => setGameType('room')}
                className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-8 border-2 border-cyan-500/30 hover:border-cyan-400/50 shadow-2xl transition-all transform hover:scale-105 text-left group"
              >
                <div className="text-4xl mb-4">📱</div>
                <h2 className="text-3xl font-black text-cyan-300 mb-3 tracking-tight">ROOM CODE</h2>
                <p className="text-cyan-200/70 text-sm leading-relaxed font-mono">
                  Create a room code. Players join on their own devices to see their roles privately.
                </p>
                <div className="mt-4 text-cyan-400 font-bold text-sm">→ Like Jackbox!</div>
              </button>
            </div>

            {/* Join Room Button */}
            <div className="text-center mt-8">
              <button
                onClick={() => setGameState('join-room')}
                className="bg-slate-700/50 hover:bg-slate-700/70 text-cyan-300 px-8 py-4 rounded-xl border-2 border-cyan-500/30 font-bold transition-all text-lg"
              >
                JOIN EXISTING ROOM
              </button>
            </div>
          </div>
        </div>
      );
    }

    return (
      <div className="min-h-screen bg-gradient-to-br from-blue-950 via-slate-900 to-indigo-950 p-4 md:p-8 font-['Space_Mono',monospace]">
        <div className="max-w-5xl mx-auto">
          {/* Header */}
          <div className="text-center mb-12 relative">
            <div className="absolute inset-0 bg-cyan-500/10 blur-3xl"></div>
            <div className="relative">
              <h1 className="text-6xl md:text-8xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-blue-400 to-indigo-400 mb-4 tracking-tighter transform -skew-y-1">
                IMPOSTER
              </h1>
              <div className="text-xl md:text-2xl text-cyan-300 font-bold tracking-widest">
                ⚽ FOOTBALL EDITION ⚽
              </div>
            </div>
            
            {/* Admin Button */}
            <button
              onClick={() => setShowPasswordPrompt(true)}
              className="absolute top-0 right-0 text-cyan-400/50 hover:text-cyan-400 transition-all"
              title="Admin Panel"
            >
              <Settings size={24} />
            </button>
          </div>

          {/* Game Mode Selection */}
          <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-6 border-2 border-cyan-500/30 shadow-2xl mb-8">
            <div className="flex items-center justify-between mb-4">
              <div className="flex items-center gap-3">
                <Tag className="text-cyan-400" size={28} />
                <h2 className="text-2xl font-black text-cyan-300 tracking-tight">GAME MODE</h2>
              </div>
              {selectedGameMode.length > 0 && (
                <button
                  onClick={clearGameModes}
                  className="bg-red-500/20 hover:bg-red-500/30 text-red-300 px-4 py-2 rounded-lg border-2 border-red-500/40 font-bold transition-all text-sm"
                >
                  CLEAR ALL
                </button>
              )}
            </div>

            {selectedGameMode.length > 0 && (
              <div className="mb-4 p-3 bg-cyan-900/20 rounded-lg border border-cyan-500/30">
                <div className="text-cyan-300 text-sm font-bold mb-1">SELECTED FILTERS:</div>
                <div className="text-cyan-400 font-mono text-sm">
                  {selectedGameMode.join(' + ')}
                </div>
              </div>
            )}
            
            {/* Position */}
            <div className="mb-4">
              <div className="text-cyan-400 text-sm font-bold mb-2">POSITION:</div>
              <div className="flex flex-wrap gap-3">
                {CATEGORIES.Position.map((category) => (
                  <button
                    key={category}
                    onClick={() => toggleGameMode(category)}
                    className={`px-6 py-3 rounded-lg font-bold transition-all border-2 ${
                      selectedGameMode.includes(category)
                        ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                        : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                    }`}
                  >
                    {selectedGameMode.includes(category) ? '✓ ' : ''}{category}
                  </button>
                ))}
              </div>
            </div>

            {/* Nation */}
            <div className="mb-4">
              <div className="text-cyan-400 text-sm font-bold mb-2">NATION:</div>
              <div className="flex flex-wrap gap-3">
                {CATEGORIES.Nation.map((category) => (
                  <button
                    key={category}
                    onClick={() => toggleGameMode(category)}
                    className={`px-6 py-3 rounded-lg font-bold transition-all border-2 ${
                      selectedGameMode.includes(category)
                        ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                        : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                    }`}
                  >
                    {selectedGameMode.includes(category) ? '✓ ' : ''}{category}
                  </button>
                ))}
              </div>
            </div>

            {/* Leagues */}
            <div className="mb-4">
              <div className="text-cyan-400 text-sm font-bold mb-2">LEAGUES:</div>
              <div className="flex flex-wrap gap-3">
                {CATEGORIES.Leagues.map((category) => (
                  <button
                    key={category}
                    onClick={() => toggleGameMode(category)}
                    className={`px-6 py-3 rounded-lg font-bold transition-all border-2 ${
                      selectedGameMode.includes(category)
                        ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                        : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                    }`}
                  >
                    {selectedGameMode.includes(category) ? '✓ ' : ''}{category}
                  </button>
                ))}
              </div>
            </div>

            {/* Age */}
            <div className="mb-4">
              <div className="text-cyan-400 text-sm font-bold mb-2">AGE:</div>
              <div className="flex flex-wrap gap-3">
                {CATEGORIES.Age.map((category) => (
                  <button
                    key={category}
                    onClick={() => toggleGameMode(category)}
                    className={`px-6 py-3 rounded-lg font-bold transition-all border-2 ${
                      selectedGameMode.includes(category)
                        ? 'bg-cyan-500/30 border-cyan-400 text-cyan-300'
                        : 'bg-slate-700/30 border-slate-600 text-slate-400 hover:border-slate-500'
                    }`}
                  >
                    {selectedGameMode.includes(category) ? '✓ ' : ''}{category}
                  </button>
                ))}
              </div>
            </div>
            
            <div className="mt-4 text-cyan-400/60 text-sm font-mono">
              {getFilteredFootballers().length} player{getFilteredFootballers().length !== 1 ? 's' : ''} available
              {selectedGameMode.length > 0 ? ' matching ALL selected filters' : ' (all players)'}
            </div>
          </div>

          {/* Players Setup */}
          <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-6 border-2 border-cyan-500/30 shadow-2xl mb-8">
            <div className="flex items-center gap-3 mb-6">
              <Users className="text-cyan-400" size={28} />
              <h2 className="text-2xl font-black text-cyan-300 tracking-tight">PLAYERS</h2>
            </div>
            
            <div className="space-y-3 mb-4 max-h-80 overflow-y-auto">
              {players.map((player, index) => (
                <div key={index} className="flex gap-2">
                  <input
                    type="text"
                    value={player}
                    onChange={(e) => updatePlayer(index, e.target.value)}
                    placeholder={`Player ${index + 1}`}
                    className="flex-1 bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono"
                  />
                  {players.length > 1 && (
                    <button
                      onClick={() => removePlayer(index)}
                      className="bg-red-500/20 hover:bg-red-500/40 text-red-300 px-4 rounded-lg border-2 border-red-500/30 transition-all"
                    >
                      ✕
                    </button>
                  )}
                </div>
              ))}
            </div>

            <button
              onClick={addPlayer}
              className="w-full bg-cyan-500/20 hover:bg-cyan-500/30 text-cyan-300 py-3 rounded-lg border-2 border-cyan-500/40 font-bold transition-all transform hover:scale-105"
            >
              + ADD PLAYER
            </button>
          </div>

          {/* Start Game Button */}
          <div className="text-center">
            <div className="flex gap-4 justify-center items-center">
              <button
                onClick={() => setGameType(null)}
                className="bg-slate-700/50 hover:bg-slate-700/70 text-slate-300 px-8 py-4 rounded-xl border-2 border-slate-500/30 font-bold transition-all text-lg"
              >
                ← BACK
              </button>
              <button
                onClick={startGame}
                className="bg-gradient-to-r from-orange-500 to-amber-500 hover:from-orange-400 hover:to-amber-400 text-slate-900 px-12 py-5 rounded-xl text-2xl font-black tracking-tight shadow-2xl transform hover:scale-105 transition-all border-4 border-orange-300/50"
              >
                {gameType === 'room' ? 'CREATE ROOM' : 'START GAME'}
              </button>
            </div>
          </div>
        </div>
      </div>
    );
  }

  // JOIN ROOM SCREEN
  if (gameState === 'join-room') {
    return (
      <div className="min-h-screen bg-gradient-to-br from-blue-950 via-slate-900 to-indigo-950 p-4 flex items-center justify-center font-['Space_Mono',monospace]">
        <div className="bg-slate-800/50 backdrop-blur-xl rounded-2xl p-8 border-2 border-cyan-500/30 shadow-2xl max-w-md w-full">
          <h2 className="text-3xl font-black text-cyan-300 tracking-tight mb-6 text-center">JOIN ROOM</h2>
          
          <div className="space-y-4">
            <div>
              <label className="text-cyan-400 font-bold text-sm mb-2 block">ROOM CODE</label>
              <input
                type="text"
                value={roomCodeInput}
                onChange={(e) => setRoomCodeInput(e.target.value.toUpperCase())}
                placeholder="BOLT-1234"
                className="w-full bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono text-center text-2xl"
                autoFocus
              />
            </div>

            <div>
              <label className="text-cyan-400 font-bold text-sm mb-2 block">YOUR NAME</label>
              <input
                type="text"
                value={playerNameInput}
                onChange={(e) => setPlayerNameInput(e.target.value)}
                placeholder="Enter your name..."
                className="w-full bg-slate-700/50 text-white px-4 py-3 rounded-lg border-2 border-cyan-500/20 focus:border-cyan-400 focus:outline-none transition-all placeholder-slate-500 font-mono"
                onKeyPress={(e) => e.key === 'Enter' && joinRoom()}
              />
            </div>

            <div className="pt-4 space-y-3">
              <button
                onClick={joinRoom}
                className="w-full bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-400 hover:to-blue-400 text-white py-4 rounded-lg font-black text-lg tracking-tight transition-all transform hover:scale-105"
              >
                JOIN GAME
              </button>
              
              <button
                onClick={() => { setGameState('setup'); setRoomCodeInput(''); setPlayerNameInput(''); }}
                className="w-full bg-slate-700/50 hover:bg-slate-700/70 text-slate-300 py-3 rounded-lg border-2 border-slate-500/30 font-bold transition-all"
              >
                BACK
              </button>
            </div>
          </div>
        </div>
      </div>
    );
  }

  // PLAYING SCREEN
  if (gameState === 'playing') {
    // Room mode - player view (only see your own role)
    if (gameType === 'room' && currentPlayerRole) {
      return (
        <div className="min-h-screen bg-gradient-to-br from-blue-950 via-slate-900 to-indigo-950 p-4 md:p-8 font-['Space_Mono',monospace] flex items-center justify-center">
          <div className="max-w-2xl w-full">
            {/* Header */}
            <div className="text-center mb-8">
              <h1 className="text-5xl md:text-7xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-blue-400 to-indigo-400 mb-4 tracking-tighter">
                YOUR ROLE
              </h1>
              <p className="text-cyan-400 text-sm font-mono">
                Room: {roomCode}
              </p>
            </div>

            {/* Player Card */}
            <div className={`relative overflow-hidden rounded-3xl border-4 shadow-2xl ${
              currentPlayerRole.isImposter
                ? 'bg-red-900/40 border-red-500/50 shadow-red-500/20'
                : 'bg-cyan-900/40 border-cyan-500/50 shadow-cyan-500/20'
            }`}>
              <div className="p-8 md:p-12 text-center">
                <h2 className="text-3xl md:text-4xl font-black text-white mb-6 tracking-tight">
                  {currentPlayerRole.name}
                </h2>
                
                <div className={`text-sm font-bold tracking-widest mb-4 ${
                  currentPlayerRole.isImposter ? 'text-red-400' : 'text-cyan-400'
                }`}>
                  {currentPlayerRole.isImposter ? '⚠️ IMPOSTER' : '✓ INNOCENT'}
                </div>
                
                <div className="text-4xl md:text-6xl font-black text-white tracking-tight">
                  {currentPlayerRole.isImposter ? (
                    <div className="text-red-400">YOU ARE THE<br/>IMPOSTER</div>
                  ) : (
                    currentPlayerRole.footballer
                  )}
                </div>
              </div>
            </div>

            {/* Instructions */}
            <div className="mt-8 bg-slate-800/30 backdrop-blur-xl rounded-xl p-6 border border-cyan-500/20">
              <h3 className="text-xl font-black text-cyan-300 mb-3 tracking-tight">REMEMBER</h3>
              <ul className="space-y-2 text-cyan-200/80 font-mono text-sm">
                <li>• Keep your role secret!</li>
                <li>• Discuss with other players to find the imposter</li>
                <li>• {currentPlayerRole.isImposter ? 'Blend in without knowing the real footballer' : 'Work together to identify who has a different player'}</li>
              </ul>
            </div>

            <div className="text-center mt-6">
              <button
                onClick={resetGame}
                className="bg-slate-700/50 hover:bg-slate-700/70 text-cyan-300 px-8 py-3 rounded-lg border-2 border-cyan-500/30 font-bold transition-all"
              >
                LEAVE GAME
              </button>
            </div>
          </div>
        </div>
      );
    }

    // Local mode or Room mode (host view)
    const showRoomCode = gameType === 'room' && roomCode;
    
    return (
      <div className="min-h-screen bg-gradient-to-br from-blue-950 via-slate-900 to-indigo-950 p-4 md:p-8 font-['Space_Mono',monospace]">
        <div className="max-w-4xl mx-auto">
          {/* Header */}
          <div className="text-center mb-8">
            <h1 className="text-5xl md:text-7xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-blue-400 to-indigo-400 mb-4 tracking-tighter">
              {showRoomCode ? 'ROOM HOST VIEW' : 'GAME IN PROGRESS'}
            </h1>
            {showRoomCode ? (
              <div className="bg-cyan-900/30 backdrop-blur-xl rounded-xl p-4 border-2 border-cyan-500/50 inline-block mb-4">
                <div className="text-cyan-300 text-sm font-bold mb-1">ROOM CODE:</div>
                <div className="text-5xl font-black text-cyan-300 tracking-wider font-mono">{roomCode}</div>
                <div className="text-cyan-400/70 text-xs mt-2">Share this code with players</div>
              </div>
            ) : (
              <p className="text-cyan-300/80 text-lg font-mono">
                Click each player's name to reveal their role
              </p>
            )}
            {selectedGameMode.length > 0 && (
              <p className="text-cyan-400 text-sm font-mono mt-2">
                Mode: {selectedGameMode.join(' + ')}
              </p>
            )}
          </div>

          {/* Controls */}
          <div className="flex gap-4 justify-center mb-8 flex-wrap">
            {!showRoomCode && (
              <button
                onClick={() => setShowAllRoles(!showAllRoles)}
                className="bg-slate-700/50 hover:bg-slate-700/70 text-cyan-300 px-6 py-3 rounded-lg border-2 border-cyan-500/30 font-bold transition-all flex items-center gap-2"
              >
                {showAllRoles ? <EyeOff size={20} /> : <Eye size={20} />}
                {showAllRoles ? 'HIDE' : 'REVEAL'} ALL
              </button>
            )}
            <button
              onClick={resetGame}
              className="bg-red-500/20 hover:bg-red-500/30 text-red-300 px-6 py-3 rounded-lg border-2 border-red-500/30 font-bold transition-all flex items-center gap-2"
            >
              <RefreshCw size={20} />
              {showRoomCode ? 'END ROOM' : 'NEW GAME'}
            </button>
          </div>

          {/* Player Cards */}
          {showRoomCode ? (
            // Room mode - just show player names
            <div className="grid md:grid-cols-2 gap-4">
              {assignments.map((assignment, index) => (
                <div
                  key={index}
                  className="bg-slate-800/50 border-2 border-cyan-500/30 rounded-2xl p-6"
                >
                  <h3 className="text-2xl font-black text-white tracking-tight">
                    {assignment.name}
                  </h3>
                  <p className="text-cyan-300/60 text-sm mt-2 font-mono">
                    Waiting to join...
                  </p>
                </div>
              ))}
            </div>
          ) : (
            // Local mode - click to reveal
            <div className="grid md:grid-cols-2 gap-4">
            {assignments.map((assignment, index) => (
              <div
                key={index}
                className={`relative overflow-hidden rounded-2xl border-2 transition-all transform hover:scale-105 cursor-pointer ${
                  showAllRoles || revealedPlayer === index
                    ? assignment.isImposter
                      ? 'bg-red-900/40 border-red-500/50 shadow-2xl shadow-red-500/20'
                      : 'bg-cyan-900/40 border-cyan-500/50 shadow-2xl shadow-cyan-500/20'
                    : 'bg-slate-800/50 border-cyan-500/30 hover:border-cyan-400/50'
                }`}
                onClick={() => !showAllRoles && revealRole(index)}
              >
                {/* Background Pattern */}
                <div className="absolute inset-0 opacity-5">
                  <div className="absolute inset-0" style={{
                    backgroundImage: 'repeating-linear-gradient(90deg, transparent, transparent 50px, rgba(255,255,255,0.03) 50px, rgba(255,255,255,0.03) 100px)',
                  }}></div>
                </div>

                <div className="relative p-6">
                  <div className="flex items-center justify-between mb-4">
                    <h3 className="text-2xl font-black text-white tracking-tight flex items-center gap-2">
                      {assignment.isImposter && (showAllRoles || revealedPlayer === index) && (
                        <UserX className="text-red-400" size={24} />
                      )}
                      {!assignment.isImposter && (showAllRoles || revealedPlayer === index) && (
                        <Shield className="text-cyan-400" size={24} />
                      )}
                      {assignment.name}
                    </h3>
                  </div>

                  {(showAllRoles || revealedPlayer === index) ? (
                    <div className="space-y-2">
                      <div className={`text-sm font-bold tracking-widest ${
                        assignment.isImposter ? 'text-red-400' : 'text-cyan-400'
                      }`}>
                        {assignment.isImposter ? '⚠️ IMPOSTER' : '✓ INNOCENT'}
                      </div>
                      <div className="text-3xl font-black text-white tracking-tight">
                        {assignment.isImposter ? (
                          <div className="text-red-400">YOU ARE THE IMPOSTER</div>
                        ) : (
                          assignment.footballer
                        )}
                      </div>
                    </div>
                  ) : (
                    <div className="text-cyan-300/50 text-lg font-mono">
                      Click to reveal...
                    </div>
                  )}
                </div>
              </div>
            ))}
          </div>
          )}

          {/* Game Info */}
          <div className="mt-8 bg-slate-800/30 backdrop-blur-xl rounded-xl p-6 border border-cyan-500/20">
            <h3 className="text-xl font-black text-cyan-300 mb-3 tracking-tight">HOW TO PLAY</h3>
            <ul className="space-y-2 text-cyan-200/80 font-mono text-sm">
              <li>• Everyone except the imposter gets the SAME footballer name</li>
              <li>• The imposter sees "YOU ARE THE IMPOSTER"</li>
              <li>• Discuss and figure out who the imposter is</li>
              <li>• The imposter tries to blend in without knowing the real footballer</li>
            </ul>
          </div>
        </div>
      </div>
    );
  }

  return null;
}
