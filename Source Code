import React, { useState, useRef } from 'react';
import { Shield, Users, Mail, Instagram, Linkedin, CheckCircle, AlertTriangle, ExternalLink, Menu, X, Send, Globe, MapPin, TrendingUp, Zap, Star, Clock } from 'lucide-react';

const NewsKnight = () => {
  const [currentPage, setCurrentPage] = useState('home');
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [newsCategory, setNewsCategory] = useState('');
  const [newsType, setNewsType] = useState('');
  const [analysisResult, setAnalysisResult] = useState(null);
  const [isAnalyzing, setIsAnalyzing] = useState(false);
  
  // Chatbot state
  const [isChatOpen, setIsChatOpen] = useState(false);
  const [chatMessages, setChatMessages] = useState([
    {
      id: 1,
      sender: 'bot',
      message: "Hi! I'm NewsKnight AI 🛡️ I can help you verify news articles and detect misinformation. Just paste any news content and I'll analyze it for you!",
      timestamp: new Date()
    }
  ]);
  const [chatInput, setChatInput] = useState('');
  const [isChatAnalyzing, setIsChatAnalyzing] = useState(false);
  
  // Use refs for input values to avoid controlled component issues
  const newsContentRef = useRef(null);
  const emailRef = useRef(null);
  const chatInputRef = useRef(null);
  const chatMessagesRef = useRef(null);
  const contactFormRefs = {
    name: useRef(null),
    email: useRef(null),
    subject: useRef(null),
    message: useRef(null)
  };

  // Chatbot analysis function
  const analyzeChatNews = async (userMessage) => {
    setIsChatAnalyzing(true);
    
    // Add user message to chat
    const userMsg = {
      id: Date.now(),
      sender: 'user',
      message: userMessage,
      timestamp: new Date()
    };
    
    setChatMessages(prev => [...prev, userMsg]);
    
    // Simulate analysis
    setTimeout(() => {
      const isNewsContent = userMessage.length > 50;
      
      if (!isNewsContent) {
        const botResponse = {
          id: Date.now() + 1,
          sender: 'bot',
          message: "I can help you verify news articles! Please share the news content you'd like me to analyze. You can paste headlines, articles, or claims that you want to fact-check. I'll analyze them for credibility and potential misinformation.",
          timestamp: new Date()
        };
        setChatMessages(prev => [...prev, botResponse]);
        setIsChatAnalyzing(false);
        return;
      }
      
      // Mock analysis result
      const mockResult = {
        credibilityScore: Math.floor(Math.random() * 40) + 40, // 40-80 range
        verdict: Math.random() > 0.5 ? "MOSTLY CREDIBLE" : "SUSPICIOUS",
        conversationalResponse: "Based on my analysis, this content shows some concerning patterns. I'd recommend cross-checking with established news sources.",
        quickTips: [
          "Check the publication date and source",
          "Look for emotional language that might indicate bias",
          "Verify claims with multiple independent sources"
        ],
        followUpQuestions: [
          "Can you help me check another article?",
          "What makes news sources reliable?"
        ]
      };
      
      const botResponse = {
        id: Date.now() + 1,
        sender: 'bot',
        message: mockResult.conversationalResponse,
        timestamp: new Date(),
        analysis: mockResult
      };
      
      setChatMessages(prev => [...prev, botResponse]);
      setIsChatAnalyzing(false);
    }, 2000);
  };

  // Handle chat message send
  const sendChatMessage = async () => {
    const message = chatInputRef.current?.value?.trim();
    if (!message) return;
    
    setChatInput('');
    if (chatInputRef.current) {
      chatInputRef.current.value = '';
    }
    
    await analyzeChatNews(message);
  };

  // Handle Enter key in chat
  const handleChatKeyPress = (e) => {
    if (e.key === 'Enter' && !e.shiftKey) {
      e.preventDefault();
      sendChatMessage();
    }
  };

  // Scroll chat to bottom
  const scrollChatToBottom = () => {
    if (chatMessagesRef.current) {
      chatMessagesRef.current.scrollTop = chatMessagesRef.current.scrollHeight;
    }
  };

  // Auto-scroll when new messages arrive
  React.useEffect(() => {
    scrollChatToBottom();
  }, [chatMessages]);

  // Enhanced fake news analysis function
  const analyzeNews = async () => {
    const newsContent = newsContentRef.current?.value || '';
    
    if (!newsContent.trim()) return;
    
    setIsAnalyzing(true);
    
    // Simulate analysis with enhanced results
    setTimeout(() => {
      const mockScore = Math.floor(Math.random() * 60) + 20; // 20-80 range
      const verdict = mockScore >= 70 ? "HIGHLY CREDIBLE" : 
                     mockScore >= 50 ? "MOSTLY CREDIBLE" : 
                     mockScore >= 30 ? "SUSPICIOUS" : "LIKELY FAKE";
      
      setAnalysisResult({
        credibilityScore: mockScore,
        verdict: verdict,
        analysis: {
          sourceReliability: `${newsCategory === 'international' ? 'International sources' : 'National sources'} analysis completed`,
          factualAccuracy: "Cross-referenced with multiple databases",
          languageAnalysis: "Content structure and tone evaluated",
          biasDetection: "Political and cultural bias patterns identified"
        },
        keyFindings: [
          `${newsCategory === 'international' ? 'Global' : 'Local'} context verification completed`,
          "Source credibility assessment performed",
          "Language pattern analysis shows standard formatting"
        ],
        recommendation: `We recommend cross-referencing with established ${newsCategory === 'international' ? 'international news agencies' : 'Indian news sources'} and fact-checkers.`,
        relatedArticles: [
          {
            title: `How to Verify ${newsCategory === 'international' ? 'International' : 'Indian'} News Sources`,
            source: `${newsCategory === 'international' ? 'Global Media Literacy' : 'Indian Fact-Checking Guide'}`,
            url: "#"
          },
          {
            title: `Common ${newsCategory === 'international' ? 'Global' : 'Indian'} Misinformation Patterns`,
            source: `${newsCategory === 'international' ? 'Reuters Fact Check' : 'Alt News Guidelines'}`,
            url: "#"
          },
          {
            title: "Best Practices for News Verification",
            source: "Media Literacy Institute",
            url: "#"
          }
        ],
        categorySpecificInsights: {
          primarySources: newsCategory === 'international' ? 'International news agencies' : 'Indian media outlets',
          contextualFactors: newsCategory === 'international' ? 'Global political climate' : 'Indian cultural context',
          verificationMethod: 'Multi-source cross-referencing'
        }
      });
      
      setIsAnalyzing(false);
    }, 3000);
  };

  const resetDetector = () => {
    setNewsCategory('');
    setNewsType('');
    setAnalysisResult(null);
    if (newsContentRef.current) {
      newsContentRef.current.value = '';
    }
  };

  const HomePage = () => (
    <div className="min-h-screen bg-black text-white">
      {/* Enhanced Hero Section */}
      <section className="relative min-h-screen flex items-center justify-center bg-gradient-to-br from-black via-gray-900 to-black overflow-hidden">
        {/* Animated background elements */}
        <div className="absolute inset-0">
          <div className="absolute top-20 left-20 w-2 h-2 bg-blue-400 rounded-full animate-pulse"></div>
          <div className="absolute top-40 right-32 w-1 h-1 bg-blue-300 rounded-full animate-ping"></div>
          <div className="absolute bottom-32 left-1/4 w-1.5 h-1.5 bg-blue-500 rounded-full animate-pulse"></div>
          <div className="absolute top-1/3 right-1/4 w-2 h-2 bg-blue-200 rounded-full animate-ping"></div>
        </div>
        
        <div className="absolute inset-0 bg-gradient-radial from-blue-500/10 to-transparent"></div>
        <div className="relative z-10 text-center px-6 max-w-5xl mx-auto">
          <div className="animate-fade-in-up">
            {/* Enhanced logo with glow effect */}
            <div className="relative mb-8">
              <Shield className="w-24 h-24 mx-auto text-blue-400 animate-pulse drop-shadow-2xl" />
              <div className="absolute inset-0 w-24 h-24 mx-auto bg-blue-400/20 rounded-full blur-xl"></div>
            </div>
            
            <h1 className="text-6xl md:text-8xl font-bold mb-6 bg-gradient-to-r from-white via-blue-200 to-white bg-clip-text text-transparent drop-shadow-lg">
              NewsKnight
            </h1>
            <p className="text-2xl md:text-3xl text-gray-300 mb-4 font-light">
              Deciphering Truth in News
            </p>
            
            {/* New tagline with stats */}
            <div className="flex flex-wrap justify-center gap-8 mb-8 text-sm text-gray-400">
              <div className="flex items-center gap-2">
                <Zap className="w-4 h-4 text-yellow-400" />
                <span>AI-Powered Analysis</span>
              </div>
              <div className="flex items-center gap-2">
                <Globe className="w-4 h-4 text-green-400" />
                <span>Global Coverage</span>
              </div>
              <div className="flex items-center gap-2">
                <Clock className="w-4 h-4 text-blue-400" />
                <span>Real-time Detection</span>
              </div>
            </div>
            
            <div className="flex flex-col sm:flex-row gap-4 justify-center">
              <button
                onClick={() => setCurrentPage('detector')}
                className="bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 px-12 py-4 rounded-full text-xl font-semibold transition-all duration-300 transform hover:scale-105 hover:shadow-2xl hover:shadow-blue-500/25"
              >
                Start Analyzing
              </button>
              <button
                onClick={() => setCurrentPage('about')}
                className="border border-gray-600 hover:border-blue-400 px-12 py-4 rounded-full text-xl font-semibold transition-all duration-300 transform hover:scale-105 hover:bg-blue-500/10"
              >
                Learn More
              </button>
            </div>
          </div>
        </div>
      </section>

      {/* Enhanced Features Section */}
      <section className="py-20 px-6 bg-gradient-to-b from-gray-900 to-black">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-4">Why Choose NewsKnight?</h2>
          <p className="text-gray-400 text-center mb-12 max-w-2xl mx-auto">
            Our cutting-edge AI technology provides comprehensive news verification with unmatched accuracy and speed.
          </p>
          
          <div className="grid md:grid-cols-3 gap-8">
            {[
              {
                icon: <Zap className="w-8 h-8" />,
                title: "Lightning Fast",
                description: "Get analysis results in seconds with our optimized AI algorithms",
                color: "text-yellow-400"
              },
              {
                icon: <Globe className="w-8 h-8" />,
                title: "Global Coverage", 
                description: "Verify news from international and national sources with context-aware analysis",
                color: "text-green-400"
              },
              {
                icon: <Star className="w-8 h-8" />,
                title: "High Accuracy",
                description: "Advanced machine learning models trained on millions of verified articles",
                color: "text-blue-400"
              }
            ].map((feature, index) => (
              <div key={index} className="group bg-gray-800/50 p-8 rounded-xl hover:bg-gray-800/80 transition-all duration-300 transform hover:-translate-y-2 hover:shadow-xl border border-gray-700 hover:border-gray-600">
                <div className={`${feature.color} mb-4 group-hover:scale-110 transition-transform duration-300`}>
                  {feature.icon}
                </div>
                <h3 className="text-xl font-semibold mb-3">{feature.title}</h3>
                <p className="text-gray-300">{feature.description}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Enhanced About Project Section */}
      <section className="py-20 px-6 bg-gray-900">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-12">About NewsKnight</h2>
          <div className="grid md:grid-cols-2 gap-12 items-center">
            <div>
              <h3 className="text-2xl font-semibold mb-6 text-blue-400">Our Mission</h3>
              <p className="text-gray-300 text-lg leading-relaxed mb-6">
                We are NewsKnight, a dedicated team committed to combating misinformation and promoting media literacy. 
                In an era where fake news spreads faster than truth, we've developed an AI-powered solution to help 
                reporters, students, and citizens identify potentially false information.
              </p>
              <p className="text-gray-300 text-lg leading-relaxed">
                Our advanced detection system analyzes news content across multiple dimensions, providing users with 
                reliable credibility assessments and educational insights to make informed decisions about the information they consume.
              </p>
            </div>
            <div className="bg-gradient-to-br from-gray-800 to-gray-900 p-8 rounded-xl border border-gray-700">
              <h4 className="text-xl font-semibold mb-6 text-blue-400">Impact Statistics</h4>
              <div className="grid grid-cols-2 gap-6">
                <div className="text-center">
                  <div className="text-3xl font-bold text-blue-400 mb-2">10K+</div>
                  <div className="text-sm text-gray-400">Articles Analyzed</div>
                </div>
                <div className="text-center">
                  <div className="text-3xl font-bold text-green-400 mb-2">95%</div>
                  <div className="text-sm text-gray-400">Accuracy Rate</div>
                </div>
                <div className="text-center">
                  <div className="text-3xl font-bold text-yellow-400 mb-2">50+</div>
                  <div className="text-sm text-gray-400">Countries Covered</div>
                </div>
                <div className="text-center">
                  <div className="text-3xl font-bold text-purple-400 mb-2">24/7</div>
                  <div className="text-sm text-gray-400">Monitoring</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Enhanced FAQ Section */}
      <section className="py-20 px-6 bg-black">
        <div className="max-w-4xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-12">Frequently Asked Questions</h2>
          <div className="space-y-6">
            {[
              {
                q: "How accurate is the NewsKnight detector?",
                a: "Our AI-powered system analyzes multiple factors including source credibility, language patterns, and cross-references with verified databases. While highly accurate, we always recommend using it as one tool among others for comprehensive fact-checking."
              },
              {
                q: "What types of news can I check?",
                a: "You can analyze both international and national (India) news across categories including Political, Finance, Sports, and general news. Our system is designed to handle various news formats and sources."
              },
              {
                q: "Is my data stored or shared?",
                a: "We prioritize your privacy. News content submitted for analysis is processed securely and not stored permanently. Please review our Privacy Policy for complete details."
              },
              {
                q: "Can I use this for professional journalism?",
                a: "Absolutely! NewsKnight is designed to assist reporters, researchers, and media professionals in their fact-checking workflows, providing detailed analysis reports suitable for professional use."
              }
            ].map((faq, index) => (
              <div key={index} className="bg-gradient-to-r from-gray-900 to-gray-800 p-6 rounded-xl border border-gray-700 hover:border-gray-600 transition-all duration-300">
                <h3 className="text-xl font-semibold mb-3 text-blue-400">{faq.q}</h3>
                <p className="text-gray-300 leading-relaxed">{faq.a}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Enhanced Articles Section */}
      <section className="py-20 px-6 bg-gray-900">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-4xl font-bold text-center mb-12">Media Literacy & Awareness</h2>
          <div className="grid md:grid-cols-3 gap-8">
            {[
              {
                title: "The Global Impact of Fake News",
                excerpt: "Understanding how misinformation spreads and affects societies worldwide.",
                category: "Analysis",
                readTime: "5 min read",
                trending: true
              },
              {
                title: "Building Media Literacy Skills",
                excerpt: "Essential techniques for identifying reliable sources and verifying information.",
                category: "Education",
                readTime: "8 min read",
                trending: false
              },
              {
                title: "The Role of AI in Fact-Checking",
                excerpt: "How artificial intelligence is revolutionizing the fight against misinformation.",
                category: "Technology",
                readTime: "6 min read",
                trending: true
              }
            ].map((article, index) => (
              <div key={index} className="group bg-gradient-to-br from-gray-800 to-gray-900 p-6 rounded-xl hover:from-gray-750 hover:to-gray-800 transition-all duration-300 border border-gray-700 hover:border-gray-600 transform hover:-translate-y-1">
                <div className="flex items-center justify-between mb-3">
                  <div className="text-blue-400 text-sm font-semibold">{article.category}</div>
                  {article.trending && (
                    <div className="flex items-center gap-1 text-orange-400 text-xs">
                      <TrendingUp className="w-3 h-3" />
                      <span>Trending</span>
                    </div>
                  )}
                </div>
                <h3 className="text-xl font-semibold mb-3 group-hover:text-blue-400 transition-colors">{article.title}</h3>
                <p className="text-gray-300 mb-4">{article.excerpt}</p>
                <div className="flex items-center justify-between">
                  <span className="text-xs text-gray-500">{article.readTime}</span>
                  <button className="text-blue-400 hover:text-blue-300 flex items-center group-hover:translate-x-1 transition-transform">
                    Read More <ExternalLink className="w-4 h-4 ml-2" />
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Enhanced Newsletter Section */}
      <section className="py-20 px-6 bg-gradient-to-r from-black via-gray-900 to-black">
        <div className="max-w-4xl mx-auto text-center">
          <h2 className="text-4xl font-bold mb-6">Stay Informed, Stay Safe</h2>
          <p className="text-gray-300 text-lg mb-8">
            Subscribe to our newsletter for the latest updates on media literacy and fact-checking tools.
          </p>
          <div className="flex flex-col sm:flex-row max-w-md mx-auto gap-4">
            <input
              type="email"
              ref={emailRef}
              placeholder="Enter your email"
              className="flex-1 px-6 py-4 bg-gray-800 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 text-white border border-gray-700"
            />
            <button 
              type="button"
              className="bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 px-8 py-4 rounded-xl font-semibold transition-all transform hover:scale-105"
            >
              Subscribe
            </button>
          </div>
        </div>
      </section>

      {/* Enhanced Footer */}
      <footer className="py-12 px-6 bg-gray-900 border-t border-gray-800">
        <div className="max-w-6xl mx-auto">
          <div className="flex flex-col md:flex-row justify-between items-center mb-8">
            <div className="flex items-center space-x-6 mb-4 md:mb-0">
              <a href="#" className="text-blue-400 hover:text-blue-300 transform hover:scale-110 transition-all">
                <Linkedin className="w-6 h-6" />
              </a>
              <a href="#" className="text-blue-400 hover:text-blue-300 transform hover:scale-110 transition-all">
                <Instagram className="w-6 h-6" />
              </a>
            </div>
            <div className="flex items-center space-x-2 text-gray-300">
              <Mail className="w-4 h-4" />
              <span>sahudibyendu75@gmail.com</span>
            </div>
          </div>
          <div className="flex flex-col md:flex-row justify-between items-center text-gray-400 text-sm">
            <div className="flex space-x-6 mb-4 md:mb-0">
              <a href="#" className="hover:text-white transition-colors">Privacy Policy</a>
              <a href="#" className="hover:text-white transition-colors">Terms & Conditions</a>
            </div>
            <div>
              © 2024 NewsKnight. All rights reserved.
            </div>
          </div>
        </div>
      </footer>
    </div>
  );

  const DetectorPage = () => (
    <div className="min-h-screen bg-black text-white py-8">
      <div className="max-w-4xl mx-auto px-6">
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold mb-4 bg-gradient-to-r from-white to-blue-200 bg-clip-text text-transparent">
            Fake News Detector
          </h1>
          <p className="text-gray-300">Analyze news content for credibility and accuracy</p>
        </div>

        {!analysisResult ? (
          <div className="space-y-8">
            {/* Enhanced Category Selection */}
            <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl border border-gray-700">
              <div className="flex items-center gap-3 mb-6">
                <Globe className="w-6 h-6 text-blue-400" />
                <h2 className="text-xl font-semibold">Select News Category</h2>
              </div>
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                <button
                  onClick={() => setNewsCategory('international')}
                  className={`group p-6 rounded-xl border-2 transition-all duration-300 transform hover:scale-105 ${
                    newsCategory === 'international'
                      ? 'border-blue-500 bg-blue-500/20 shadow-lg shadow-blue-500/25'
                      : 'border-gray-600 hover:border-gray-500 hover:bg-gray-800/50'
                  }`}
                >
                  <div className="flex items-center gap-3 mb-3">
                    <Globe className={w-5 h-5 ${newsCategory === 'international' ? 'text-blue-400' : 'text-gray-400'}} />
                    <span className="font-semibold">International News</span>
                  </div>
                  <p className="text-sm text-gray-400 text-left">Global news coverage with international fact-checking standards</p>
                </button>
                <button
                  onClick={() => setNewsCategory('national')}
                  className={`group p-6 rounded-xl border-2 transition-all duration-300 transform hover:scale-105 ${
                    newsCategory === 'national'
                      ? 'border-blue-500 bg-blue-500/20 shadow-lg shadow-blue-500/25'
                      : 'border-gray-600 hover:border-gray-500 hover:bg-gray-800/50'
                  }`}
                >
                  <div className="flex items-center gap-3 mb-3">
                    <MapPin className={w-5 h-5 ${newsCategory === 'national' ? 'text-blue-400' : 'text-gray-400'}} />
                    <span className="font-semibold">National News (India)</span>
                  </div>
                  <p className="text-sm text-gray-400 text-left">Indian news with local context and cultural awareness</p>
                </button>
              </div>
            </div>

            {/* Enhanced News Type Selection */}
            {newsCategory && (
              <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl border border-gray-700 animate-fade-in">
                <h2 className="text-xl font-semibold mb-6">Select News Type</h2>
                <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
                  {['Political', 'Finance', 'Sports', 'Not Sure'].map((type) => (
                    <button
                      key={type}
                      onClick={() => setNewsType(type)}
                      className={`p-4 rounded-xl border-2 transition-all duration-300 transform hover:scale-105 ${
                        newsType === type
                          ? 'border-blue-500 bg-blue-500/20 shadow-lg shadow-blue-500/25'
                          : 'border-gray-600 hover:border-gray-500 hover:bg-gray-800/50'
                      }`}
                    >
                      <span className="font-medium">{type}</span>
                    </button>
                  ))}
                </div>
              </div>
            )}

            {/* Enhanced News Content Input */}
            {newsType && (
              <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl border border-gray-700 animate-fade-in">
                <h2 className="text-xl font-semibold mb-6">Enter News Content</h2>
                <div className="relative">
                  <textarea
                    ref={newsContentRef}
                    placeholder="Paste the news article or headline you want to verify..."
                    className="w-full h-48 p-6 bg-gray-800 rounded-xl resize-none focus:outline-none focus:ring-2 focus:ring-blue-500 text-white border border-gray-700 transition-all"
                  />
                  <div className="absolute bottom-4 right-4 text-xs text-gray-500">
                    Tip: Longer content provides more accurate analysis
                  </div>
                </div>
              </div>
            )}

            {/* Enhanced Analyze Button */}
            {newsType && (
              <div className="text-center">
                <button
                  onClick={analyzeNews}
                  disabled={isAnalyzing}
                  className="relative overflow-hidden bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 px-12 py-4 rounded-xl text-lg font-semibold transition-all duration-300 transform hover:scale-105 disabled:opacity-50 disabled:cursor-not-allowed shadow-lg shadow-blue-500/25"
                >
                  {isAnalyzing ? (
                    <div className="flex items-center gap-3">
                      <div className="w-5 h-5 border-2 border-white border-t-transparent rounded-full animate-spin"></div>
                      <span>Analyzing...</span>
                    </div>
                  ) : (
                    <div className="flex items-center gap-3">
                      <Shield className="w-5 h-5" />
                      <span>Check for Fake News</span>
                    </div>
                  )}
                </button>
              </div>
            )}
          </div>
        ) : (
          <div className="space-y-8">
            {/* Enhanced Analysis Results */}
            <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl border border-gray-700">
              <div className="flex items-center justify-between mb-8">
                <h2 className="text-2xl font-bold">Analysis Results</h2>
                <div className={`px-6 py-3 rounded-full text-sm font-semibold shadow-lg ${
                  analysisResult.credibilityScore >= 80 ? 'bg-green-500/20 text-green-400 border border-green-500/30' :
                  analysisResult.credibilityScore >= 60 ? 'bg-yellow-500/20 text-yellow-400 border border-yellow-500/30' :
                  'bg-red-500/20 text-red-400 border border-red-500/30'
                }`}>
                  {analysisResult.verdict}
                </div>
              </div>

              {/* Enhanced Credibility Score Display */}
              <div className="grid md:grid-cols-2 gap-8 mb-8">
                <div className="bg-gray-800/50 p-6 rounded-xl">
                  <h3 className="text-lg font-semibold mb-4 flex items-center gap-2">
                    <TrendingUp className="w-5 h-5 text-blue-400" />
                    Credibility Score
                  </h3>
                  <div className="space-y-4">
                    <div className="flex items-center justify-between">
                      <span className="text-3xl font-bold">{analysisResult.credibilityScore}%</span>
                      <div className={`w-6 h-6 rounded-full shadow-lg ${
                        analysisResult.credibilityScore >= 80 ? 'bg-green-400' :
                        analysisResult.credibilityScore >= 60 ? 'bg-yellow-400' :
                        'bg-red-400'
                      }`}></div>
                    </div>
                    <div className="w-full bg-gray-700 rounded-full h-3 overflow-hidden">
                      <div 
                        className={`h-3 rounded-full transition-all duration-1000 ${
                          analysisResult.credibilityScore >= 80 ? 'bg-gradient-to-r from-green-400 to-green-500' :
                          analysisResult.credibilityScore >= 60 ? 'bg-gradient-to-r from-yellow-400 to-yellow-500' :
                          'bg-gradient-to-r from-red-400 to-red-500'
                        }`}
                        style={{ width: ${analysisResult.credibilityScore}% }}
                      ></div>
                    </div>
                    <div className="text-sm text-gray-400">
                      {analysisResult.credibilityScore >= 80 ? 'Highly trustworthy content' :
                       analysisResult.credibilityScore >= 60 ? 'Generally reliable with minor concerns' :
                       analysisResult.credibilityScore >= 40 ? 'Questionable reliability' :
                       'High risk of misinformation'}
                    </div>
                  </div>
                </div>

                <div className="bg-gray-800/50 p-6 rounded-xl">
                  <h3 className="text-lg font-semibold mb-4 flex items-center gap-2">
                    <AlertTriangle className="w-5 h-5 text-yellow-400" />
                    Key Findings
                  </h3>
                  <ul className="space-y-3">
                    {analysisResult.keyFindings.map((finding, index) => (
                      <li key={index} className="flex items-start gap-3">
                        <div className="w-2 h-2 bg-yellow-400 rounded-full mt-2 flex-shrink-0"></div>
                        <span className="text-sm text-gray-300">{finding}</span>
                      </li>
                    ))}
                  </ul>
                </div>
              </div>

              {/* Enhanced Detailed Analysis */}
              <div className="bg-gray-800/30 p-6 rounded-xl mb-8">
                <h3 className="text-lg font-semibold mb-6 flex items-center gap-2">
                  <Shield className="w-5 h-5 text-blue-400" />
                  Detailed Analysis
                </h3>
                <div className="grid md:grid-cols-2 gap-6">
                  <div className="space-y-4">
                    <div className="bg-gray-700/50 p-4 rounded-lg">
                      <div className="flex items-center gap-2 mb-2">
                        <div className="w-3 h-3 bg-blue-400 rounded-full"></div>
                        <strong className="text-blue-400">Source Reliability</strong>
                      </div>
                      <p className="text-gray-300 text-sm">{analysisResult.analysis.sourceReliability}</p>
                    </div>
                    <div className="bg-gray-700/50 p-4 rounded-lg">
                      <div className="flex items-center gap-2 mb-2">
                        <div className="w-3 h-3 bg-green-400 rounded-full"></div>
                        <strong className="text-green-400">Factual Accuracy</strong>
                      </div>
                      <p className="text-gray-300 text-sm">{analysisResult.analysis.factualAccuracy}</p>
                    </div>
                  </div>
                  <div className="space-y-4">
                    <div className="bg-gray-700/50 p-4 rounded-lg">
                      <div className="flex items-center gap-2 mb-2">
                        <div className="w-3 h-3 bg-purple-400 rounded-full"></div>
                        <strong className="text-purple-400">Language Analysis</strong>
                      </div>
                      <p className="text-gray-300 text-sm">{analysisResult.analysis.languageAnalysis}</p>
                    </div>
                    <div className="bg-gray-700/50 p-4 rounded-lg">
                      <div className="flex items-center gap-2 mb-2">
                        <div className="w-3 h-3 bg-orange-400 rounded-full"></div>
                        <strong className="text-orange-400">Bias Detection</strong>
                      </div>
                      <p className="text-gray-300 text-sm">{analysisResult.analysis.biasDetection}</p>
                    </div>
                  </div>
                </div>
              </div>

              {/* Enhanced Recommendation */}
              <div className="bg-gradient-to-r from-blue-900/30 to-blue-800/30 p-6 rounded-xl mb-8 border border-blue-500/20">
                <h3 className="text-lg font-semibold mb-3 text-blue-400 flex items-center gap-2">
                  <CheckCircle className="w-5 h-5" />
                  Our Recommendation
                </h3>
                <p className="text-gray-300 leading-relaxed">{analysisResult.recommendation}</p>
              </div>

              {/* Category-Specific Insights */}
              {analysisResult.categorySpecificInsights && (
                <div className="bg-gradient-to-r from-purple-900/30 to-purple-800/30 p-6 rounded-xl mb-8 border border-purple-500/20">
                  <h3 className="text-lg font-semibold mb-4 text-purple-400 flex items-center gap-2">
                    <Globe className="w-5 h-5" />
                    Category-Specific Analysis
                  </h3>
                  <div className="grid md:grid-cols-3 gap-6">
                    <div className="bg-purple-800/20 p-4 rounded-lg">
                      <strong className="text-purple-400 block mb-2">Primary Sources</strong>
                      <p className="text-gray-300 text-sm">{analysisResult.categorySpecificInsights.primarySources}</p>
                    </div>
                    <div className="bg-purple-800/20 p-4 rounded-lg">
                      <strong className="text-purple-400 block mb-2">Contextual Factors</strong>
                      <p className="text-gray-300 text-sm">{analysisResult.categorySpecificInsights.contextualFactors}</p>
                    </div>
                    <div className="bg-purple-800/20 p-4 rounded-lg">
                      <strong className="text-purple-400 block mb-2">Verification Method</strong>
                      <p className="text-gray-300 text-sm">{analysisResult.categorySpecificInsights.verificationMethod}</p>
                    </div>
                  </div>
                </div>
              )}
            </div>

            {/* Enhanced Related Articles */}
            <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl border border-gray-700">
              <h2 className="text-xl font-semibold mb-6 flex items-center gap-2">
                <ExternalLink className="w-5 h-5 text-blue-400" />
                Related Resources
              </h2>
              <div className="grid md:grid-cols-3 gap-4">
                {analysisResult.relatedArticles.map((article, index) => (
                  <div key={index} className="bg-gray-800/50 p-5 rounded-xl hover:bg-gray-800/80 transition-all duration-300 transform hover:-translate-y-1 border border-gray-700 hover:border-gray-600">
                    <div className="flex items-start justify-between mb-3">
                      <h3 className="font-semibold text-sm leading-tight">{article.title}</h3>
                      <ExternalLink className="w-4 h-4 text-blue-400 flex-shrink-0 ml-2" />
                    </div>
                    <p className="text-xs text-gray-400 mb-3">{article.source}</p>
                    <button className="text-xs text-blue-400 hover:text-blue-300 font-medium">
                      Read More →
                    </button>
                  </div>
                ))}
              </div>
            </div>

            {/* Enhanced Action Buttons */}
            <div className="flex flex-col sm:flex-row justify-center gap-4">
              <button
                onClick={resetDetector}
                className="bg-gray-700 hover:bg-gray-600 px-8 py-3 rounded-xl font-semibold transition-all duration-300 transform hover:scale-105 border border-gray-600 hover:border-gray-500"
              >
                Check Another Article
              </button>
              <button
                onClick={() => setCurrentPage('home')}
                className="bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 px-8 py-3 rounded-xl font-semibold transition-all duration-300 transform hover:scale-105 shadow-lg shadow-blue-500/25"
              >
                Back to Home
              </button>
            </div>
          </div>
        )}
      </div>
    </div>
  );

  const AboutPage = () => (
    <div className="min-h-screen bg-black text-white py-16">
      <div className="max-w-6xl mx-auto px-6">
        <div className="text-center mb-16">
          <h1 className="text-5xl font-bold mb-6 bg-gradient-to-r from-white to-blue-200 bg-clip-text text-transparent">
            About NewsKnight
          </h1>
          <p className="text-xl text-gray-300 max-w-3xl mx-auto">
            Meet the dedicated team behind the fight against misinformation
          </p>
        </div>

        {/* Enhanced Team Section */}
        <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-8 mb-16">
          {[
            {
              name: "Ardhendu Sahu",
              role: "Team Leader",
              description: "Leading the charge against misinformation with innovative AI solutions.",
              color: "from-blue-500 to-blue-700"
            },
            {
              name: "Sayan Sengupta",
              role: "Developer",
              description: "Building robust systems for accurate news verification and analysis.",
              color: "from-green-500 to-green-700"
            },
            {
              name: "Kaustuv Ghosh",
              role: "Developer",
              description: "Crafting user experiences that make fact-checking accessible to everyone.",
              color: "from-purple-500 to-purple-700"
            },
            
          ].map((member, index) => (
            <div key={index} className="group bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl text-center hover:from-gray-800 hover:to-gray-700 transition-all duration-300 transform hover:-translate-y-2 hover:shadow-xl border border-gray-700 hover:border-gray-600">
              <div className={w-24 h-24 bg-gradient-to-br ${member.color} rounded-full mx-auto mb-6 flex items-center justify-center shadow-lg group-hover:scale-110 transition-transform duration-300}>
                <Users className="w-12 h-12 text-white" />
              </div>
              <h3 className="text-xl font-bold mb-2 group-hover:text-blue-400 transition-colors">{member.name}</h3>
              <p className="text-blue-400 font-semibold mb-4">{member.role}</p>
              <p className="text-gray-300 text-sm leading-relaxed">{member.description}</p>
            </div>
          ))}
        </div>

        {/* Enhanced Commitment Section */}
        <div className="bg-gradient-to-r from-gray-900 via-gray-800 to-gray-900 p-10 rounded-xl border border-gray-700">
          <h2 className="text-3xl font-bold mb-8 text-center bg-gradient-to-r from-white to-blue-200 bg-clip-text text-transparent">
            Our Commitment
          </h2>
          <div className="grid md:grid-cols-2 gap-8 items-center">
            <div>
              <p className="text-lg text-gray-300 leading-relaxed mb-6">
                At NewsKnight, we believe that access to accurate information is fundamental to a healthy democracy. 
                Our team is committed to making a positive impact on our environment by providing cutting-edge tools 
                that help individuals and organizations identify and combat misinformation.
              </p>
              <p className="text-lg text-gray-300 leading-relaxed">
                We're not just building technology – we're fostering a more informed and media-literate society.
              </p>
            </div>
            <div className="grid grid-cols-2 gap-4">
              <div className="bg-blue-900/30 p-6 rounded-xl text-center border border-blue-500/20">
                <div className="text-2xl font-bold text-blue-400 mb-2">100%</div>
                <div className="text-sm text-gray-400">Commitment to Truth</div>
              </div>
              <div className="bg-green-900/30 p-6 rounded-xl text-center border border-green-500/20">
                <div className="text-2xl font-bold text-green-400 mb-2">24/7</div>
                <div className="text-sm text-gray-400">Available Support</div>
              </div>
              <div className="bg-purple-900/30 p-6 rounded-xl text-center border border-purple-500/20">
                <div className="text-2xl font-bold text-purple-400 mb-2">AI</div>
                <div className="text-sm text-gray-400">Powered Technology</div>
              </div>
              <div className="bg-orange-900/30 p-6 rounded-xl text-center border border-orange-500/20">
                <div className="text-2xl font-bold text-orange-400 mb-2">Open</div>
                <div className="text-sm text-gray-400">Source Mission</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );

  const ContactPage = () => (
    <div className="min-h-screen bg-black text-white py-16">
      <div className="max-w-4xl mx-auto px-6">
        <div className="text-center mb-12">
          <h1 className="text-4xl font-bold mb-4 bg-gradient-to-r from-white to-blue-200 bg-clip-text text-transparent">
            Contact Us
          </h1>
          <p className="text-gray-300 text-lg">
            Get in touch with the NewsKnight team
          </p>
        </div>

        <div className="grid md:grid-cols-2 gap-12">
          {/* Enhanced Contact Form */}
          <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-8 rounded-xl border border-gray-700">
            <h2 className="text-2xl font-semibold mb-6 flex items-center gap-2">
              <Send className="w-6 h-6 text-blue-400" />
              Send us a Message
            </h2>
            <form className="space-y-6">
              <div>
                <label className="block text-sm font-medium mb-2 text-gray-300">Full Name</label>
                <input
                  type="text"
                  ref={contactFormRefs.name}
                  className="w-full px-4 py-3 bg-gray-800 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 text-white border border-gray-700 transition-all"
                  placeholder="Enter your name"
                />
              </div>
              <div>
                <label className="block text-sm font-medium mb-2 text-gray-300">Email Address</label>
                <input
                  type="email"
                  ref={contactFormRefs.email}
                  className="w-full px-4 py-3 bg-gray-800 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 text-white border border-gray-700 transition-all"
                  placeholder="Enter your email"
                />
              </div>
              <div>
                <label className="block text-sm font-medium mb-2 text-gray-300">Subject</label>
                <input
                  type="text"
                  ref={contactFormRefs.subject}
                  className="w-full px-4 py-3 bg-gray-800 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 text-white border border-gray-700 transition-all"
                  placeholder="Enter subject"
                />
              </div>
              <div>
                <label className="block text-sm font-medium mb-2 text-gray-300">Message</label>
                <textarea
                  rows={6}
                  ref={contactFormRefs.message}
                  className="w-full px-4 py-3 bg-gray-800 rounded-xl resize-none focus:outline-none focus:ring-2 focus:ring-blue-500 text-white border border-gray-700 transition-all"
                  placeholder="Enter your message"
                />
              </div>
              <button
                type="button"
                onClick={() => {
                  const formData = {
                    name: contactFormRefs.name.current?.value || '',
                    email: contactFormRefs.email.current?.value || '',
                    subject: contactFormRefs.subject.current?.value || '',
                    message: contactFormRefs.message.current?.value || ''
                  };
                  console.log('Form submitted:', formData);
                }}
                className="w-full bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 py-3 rounded-xl font-semibold transition-all duration-300 transform hover:scale-105 shadow-lg shadow-blue-500/25"
              >
                Send Message
              </button>
            </form>
          </div>

          {/* Enhanced Contact Info */}
          <div className="space-y-8">
            <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-6 rounded-xl border border-gray-700">
              <h3 className="text-xl font-semibold mb-4 flex items-center gap-2">
                <Mail className="w-5 h-5 text-blue-400" />
                Contact Information
              </h3>
              <div className="space-y-4">
                <div className="flex items-center gap-3 p-3 bg-gray-800/50 rounded-lg">
                  <Mail className="w-5 h-5 text-blue-400" />
                  <span>sahudibyendu75@gmail.com</span>
                </div>
              </div>
            </div>

            <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-6 rounded-xl border border-gray-700">
              <h3 className="text-xl font-semibold mb-4">Follow Us</h3>
              <div className="flex space-x-4">
                <a href="#" className="bg-blue-600 p-4 rounded-xl hover:bg-blue-700 transition-all duration-300 transform hover:scale-110 shadow-lg">
                  <Linkedin className="w-5 h-5" />
                </a>
                <a href="#" className="bg-gradient-to-r from-pink-500 to-purple-600 p-4 rounded-xl hover:from-pink-600 hover:to-purple-700 transition-all duration-300 transform hover:scale-110 shadow-lg">
                  <Instagram className="w-5 h-5" />
                </a>
              </div>
            </div>

            <div className="bg-gradient-to-br from-gray-900 to-gray-800 p-6 rounded-xl border border-gray-700">
              <h3 className="text-xl font-semibold mb-4 flex items-center gap-2">
                <Clock className="w-5 h-5 text-green-400" />
                Response Time
              </h3>
              <p className="text-gray-300 leading-relaxed">
                We typically respond to all inquiries within 24-48 hours. 
                For urgent matters, please mention "URGENT" in your subject line.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );

  return (
    <div className="bg-black min-h-screen">
      {/* Enhanced Navigation */}
      <nav className="fixed top-0 w-full bg-black/95 backdrop-blur-sm z-50 border-b border-gray-800">
        <div className="max-w-6xl mx-auto px-6 py-4">
          <div className="flex items-center justify-between">
            <div className="flex items-center space-x-3">
              <div className="relative">
                <Shield className="w-8 h-8 text-blue-400" />
                <div className="absolute inset-0 w-8 h-8 bg-blue-400/20 rounded blur-sm"></div>
              </div>
              <span className="text-xl font-bold bg-gradient-to-r from-white to-blue-200 bg-clip-text text-transparent">
                NewsKnight
              </span>
            </div>
            
            {/* Desktop Navigation */}
            <div className="hidden md:flex items-center space-x-8">
              {[
                { id: 'home', label: 'Home' },
                { id: 'detector', label: 'Detector' },
                { id: 'about', label: 'About' },
                { id: 'contact', label: 'Contact' }
              ].map((item) => (
                <button
                  key={item.id}
                  onClick={() => setCurrentPage(item.id)}
                  className={`relative px-3 py-2 rounded-lg font-medium transition-all duration-300 ${
                    currentPage === item.id 
                      ? 'text-blue-400 bg-blue-500/10' 
                      : 'text-white hover:text-blue-400 hover:bg-gray-800/50'
                  }`}
                >
                  {item.label}
                  {currentPage === item.id && (
                    <div className="absolute bottom-0 left-0 right-0 h-0.5 bg-blue-400 rounded-full"></div>
                  )}
                </button>
              ))}
            </div>

            {/* Mobile Menu Button */}
            <button
              onClick={() => setIsMenuOpen(!isMenuOpen)}
              className="md:hidden text-white p-2 rounded-lg hover:bg-gray-800 transition-colors"
            >
              {isMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
            </button>
          </div>

          {/* Enhanced Mobile Navigation */}
          {isMenuOpen && (
            <div className="md:hidden mt-4 pb-4 border-t border-gray-800 animate-fade-in">
              <div className="flex flex-col space-y-2 mt-4">
                {[
                  { id: 'home', label: 'Home' },
                  { id: 'detector', label: 'Detector' },
                  { id: 'about', label: 'About' },
                  { id: 'contact', label: 'Contact' }
                ].map((item) => (
                  <button
                    key={item.id}
                    onClick={() => {
                      setCurrentPage(item.id);
                      setIsMenuOpen(false);
                    }}
                    className={`text-left px-4 py-3 rounded-lg font-medium transition-all duration-300 ${
                      currentPage === item.id 
                        ? 'text-blue-400 bg-blue-500/10' 
                        : 'text-white hover:text-blue-400 hover:bg-gray-800/50'
                    }`}
                  >
                    {item.label}
                  </button>
                ))}
              </div>
            </div>
          )}
        </div>
      </nav>

      {/* Page Content */}
      <div className="pt-20">
        {currentPage === 'home' && <HomePage />}
        {currentPage === 'detector' && <DetectorPage />}
        {currentPage === 'about' && <AboutPage />}
        {currentPage === 'contact' && <ContactPage />}
      </div>

      {/* Enhanced Chatbot Widget */}
      <div className="fixed bottom-6 right-6 z-50">
        {/* Enhanced Chat Window */}
        {isChatOpen && (
          <div className="bg-gradient-to-br from-gray-900 to-gray-800 rounded-xl shadow-2xl border border-gray-700 mb-4 w-96 h-96 flex flex-col backdrop-blur-sm">
            {/* Enhanced Chat Header */}
            <div className="bg-gradient-to-r from-blue-600 to-blue-700 rounded-t-xl p-4 flex items-center justify-between">
              <div className="flex items-center space-x-3">
                <div className="relative">
                  <Shield className="w-5 h-5 text-white" />
                  <div className="absolute -top-1 -right-1 w-3 h-3 bg-green-400 rounded-full animate-pulse"></div>
                </div>
                <div>
                  <span className="font-semibold text-white">NewsKnight AI</span>
                  <div className="text-xs text-blue-100">Online</div>
                </div>
              </div>
              <button
                onClick={() => setIsChatOpen(false)}
                className="text-white hover:text-gray-200 p-1 rounded-lg hover:bg-white/10 transition-all"
              >
                <X className="w-5 h-5" />
              </button>
            </div>

            {/* Enhanced Chat Messages */}
            <div 
              ref={chatMessagesRef}
              className="flex-1 p-4 overflow-y-auto space-y-4 bg-gray-800/30"
            >
              {chatMessages.map((msg) => (
                <div key={msg.id} className={flex ${msg.sender === 'user' ? 'justify-end' : 'justify-start'}}>
                  <div className={`max-w-xs px-4 py-3 rounded-xl shadow-lg ${
                    msg.sender === 'user' 
                      ? 'bg-gradient-to-r from-blue-600 to-blue-700 text-white' 
                      : 'bg-gray-700 text-gray-200 border border-gray-600'
                  }`}>
                    <p className="text-sm leading-relaxed">{msg.message}</p>
                    
                    {/* Enhanced analysis results display */}
                    {msg.analysis && (
                      <div className="mt-4 pt-4 border-t border-gray-600">
                        <div className="flex items-center justify-between mb-3">
                          <span className="text-xs font-semibold flex items-center gap-1">
                            <Shield className="w-3 h-3" />
                            Analysis Results
                          </span>
                          <span className={`text-xs px-3 py-1 rounded-full font-medium ${
                            msg.analysis.credibilityScore >= 80 ? 'bg-green-600 text-green-100' :
                            msg.analysis.credibilityScore >= 60 ? 'bg-yellow-600 text-yellow-100' :
                            'bg-red-600 text-red-100'
                          }`}>
                            {msg.analysis.verdict}
                          </span>
                        </div>
                        <div className="text-xs mb-3">
                          <div className="flex items-center justify-between mb-1">
                            <strong>Credibility Score</strong>
                            <span className="font-bold">{msg.analysis.credibilityScore}%</span>
                          </div>
                          <div className="w-full bg-gray-600 rounded-full h-1.5">
                            <div 
                              className={`h-1.5 rounded-full transition-all duration-500 ${
                                msg.analysis.credibilityScore >= 80 ? 'bg-green-400' :
                                msg.analysis.credibilityScore >= 60 ? 'bg-yellow-400' :
                                'bg-red-400'
                              }`}
                              style={{ width: ${msg.analysis.credibilityScore}% }}
                            ></div>
                          </div>
                        </div>
                        
                        {/* Quick Tips */}
                        {msg.analysis.quickTips && (
                          <div className="mt-3">
                            <div className="text-xs font-semibold mb-2 flex items-center gap-1">
                              <div className="w-2 h-2 bg-yellow-400 rounded-full"></div>
                              Quick Tips
                            </div>
                            <ul className="text-xs space-y-1 text-gray-300">
                              {msg.analysis.quickTips.map((tip, index) => (
                                <li key={index} className="flex items-start gap-2">
                                  <span className="text-yellow-400 mt-0.5">•</span>
                                  <span>{tip}</span>
                                </li>
                              ))}
                            </ul>
                          </div>
                        )}
                        
                        {/* Follow-up Questions */}
                        {msg.analysis.followUpQuestions && (
                          <div className="mt-3">
                            <div className="text-xs font-semibold mb-2 flex items-center gap-1">
                              <div className="w-2 h-2 bg-blue-400 rounded-full"></div>
                              Ask me
                            </div>
                            <div className="space-y-1">
                              {msg.analysis.followUpQuestions.map((question, index) => (
                                <button
                                  key={index}
                                  onClick={() => {
                                    if (chatInputRef.current) {
                                      chatInputRef.current.value = question;
                                    }
                                  }}
                                  className="block text-xs text-blue-300 hover:text-blue-200 hover:bg-blue-900/30 px-2 py-1 rounded transition-all w-full text-left"
                                >
                                  "{question}"
                                </button>
                              ))}
                            </div>
                          </div>
                        )}
                      </div>
                    )}
                    
                    <div className="text-xs opacity-60 mt-2">
                      {msg.timestamp.toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}
                    </div>
                  </div>
                </div>
              ))}
              
              {/* Enhanced Typing indicator */}
              {isChatAnalyzing && (
                <div className="flex justify-start">
                  <div className="bg-gray-700 text-gray-200 px-4 py-3 rounded-xl max-w-xs border border-gray-600">
                    <div className="flex items-center space-x-2">
                       <div className="flex space-x-1">
                        <div className="w-2 h-2 bg-gray-400 rounded-full animate-pulse"></div>
                        <div className="w-2 h-2 bg-gray-400 rounded-full animate-pulse" style={{animationDelay: '0.2s'}}></div>
                        <div className="w-2 h-2 bg-gray-400 rounded-full animate-pulse" style={{animationDelay: '0.4s'}}></div>
                      </div>
                      <span className="text-xs text-gray-400">Analyzing...</span>
                    </div>
                  </div>
                </div>
              )}
            </div>

            {/* Enhanced Chat Input */}
            <div className="p-4 border-t border-gray-700 bg-gray-800/50">
              <div className="flex space-x-3">
                <input
                  ref={chatInputRef}
                  type="text"
                  placeholder="Paste news content to verify..."
                  className="flex-1 px-4 py-3 bg-gray-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 border border-gray-600 transition-all"
                  onKeyPress={handleChatKeyPress}
                  disabled={isChatAnalyzing}
                />
                <button
                  onClick={sendChatMessage}
                  disabled={isChatAnalyzing}
                  className="bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 px-4 py-3 rounded-xl disabled:opacity-50 transition-all duration-300 transform hover:scale-105 shadow-lg"
                >
                  <Send className="w-4 h-4 text-white" />
                </button>
              </div>
            </div>
          </div>
        )}

        {/* Enhanced Chat Toggle Button */}
        <button
          onClick={() => setIsChatOpen(!isChatOpen)}
          className="relative bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 w-16 h-16 rounded-full flex items-center justify-center shadow-2xl transition-all duration-300 transform hover:scale-110 border-2 border-blue-500/30"
        >
          {isChatOpen ? (
            <X className="w-6 h-6 text-white" />
          ) : (
            <div className="relative">
              <Shield className="w-6 h-6 text-white" />
              <div className="absolute -top-1 -right-1 w-3 h-3 bg-green-400 rounded-full animate-pulse"></div>
            </div>
          )}
          
          {/* Pulse effect */}
          <div className="absolute inset-0 rounded-full bg-blue-400/20 animate-ping"></div>
        </button>
      </div>
    </div>
  );
};

export default NewsKnight;
        
