import React, { useState } from 'react';
import { Search, Heart, Book, User, Star, DollarSign, ChevronLeft, ChevronRight, Bell, Video, Home } from 'lucide-react';

const TeachingRoomApp = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [popularTab, setPopularTab] = useState('realtime');
  const [shortVideoTab, setShortVideoTab] = useState('popular');
  
  // 카테고리 정의
  const categories = [
    { id: 'cat1', name: '카테고리1' },
    { id: 'cat2', name: '카테고리2' },
    { id: 'cat3', name: '카테고리3' },
    { id: 'cat4', name: '카테고리4' },
    { id: 'cat5', name: '카테고리5' },
    { id: 'cat6', name: '카테고리6' },
    { id: 'cat7', name: '카테고리7' },
    { id: 'cat8', name: '카테고리8' },
    { id: 'cat9', name: '카테고리9' }
  ];

  return (
    <div className="flex flex-col min-h-screen bg-gray-50">
      {/* 상단 로고와 검색창 영역 */}
      <div className="sticky top-0 z-50 bg-white shadow-md">
        <div className="container mx-auto px-4 py-3 flex items-center justify-between">
          <div className="flex items-center space-x-4">
            {/* 로고 */}
            <div className="w-36 h-10 bg-gray-100 border border-dashed border-gray-300 rounded flex items-center justify-center">
              <span className="text-gray-400 text-xs">로고 이미지</span>
            </div>
            
            {/* 검색창 */}
            <div className="relative">
              <input 
                type="text" 
                placeholder="강의명, 강사명, 키워드 검색" 
                className="w-64 pl-10 pr-4 py-2 border rounded-full focus:outline-none focus:ring-2 focus:ring-yellow-300"
              />
              <Search className="absolute left-3 top-2.5 h-5 w-5 text-gray-400" />
            </div>
          </div>
          
          {/* 로그인 상태에 따른 표시 */}
          {isLoggedIn ? (
            <div className="w-10 h-10 rounded-full bg-gray-300 flex items-center justify-center">
              <span className="text-gray-600">사</span>
            </div>
          ) : (
            <button 
              className="bg-yellow-400 text-white px-4 py-2 rounded-md hover:bg-yellow-500"
              onClick={() => setIsLoggedIn(true)}
            >
              로그인
            </button>
          )}
        </div>
      </div>
        
      {/* 탭 고정 메뉴 - 별도의 줄에 완전히 분리 */}
      <div className="sticky top-16 z-40 bg-gray-50 shadow-sm border-t border-gray-200">
        <div className="container mx-auto px-4">
          <nav className="flex justify-center md:justify-start py-3">
            <button className="text-yellow-400 font-bold flex items-center px-4 py-2 mx-1 rounded-md hover:bg-yellow-50">
              <Home className="h-5 w-5 sm:mr-1" />
              <span className="hidden sm:inline">홈</span>
            </button>
            <button className="text-gray-600 font-bold flex items-center px-4 py-2 mx-1 rounded-md hover:bg-yellow-50">
              <Heart className="h-5 w-5 sm:mr-1" /> 
              <span className="hidden sm:inline">찜한 강의</span>
            </button>
            <button className="text-gray-600 font-bold flex items-center px-4 py-2 mx-1 rounded-md hover:bg-yellow-50">
              <Book className="h-5 w-5 sm:mr-1" /> 
              <span className="hidden sm:inline">수강중 강의</span>
            </button>
            <button className="text-gray-600 font-bold flex items-center px-4 py-2 mx-1 rounded-md hover:bg-yellow-50">
              <User className="h-5 w-5 sm:mr-1" /> 
              <span className="hidden sm:inline">마이페이지</span>
            </button>
          </nav>
        </div>
      </div>
      
      <main className="flex-grow">
        {/* 프로모션 영역 */}
        <section className="bg-gray-50 py-6">
          <div className="container mx-auto px-4">
            <div className="relative overflow-hidden rounded-lg h-64 border-2 border-dashed border-gray-300 flex flex-col items-center justify-center">
              <div className="text-center p-8">
                <div className="w-16 h-16 bg-yellow-100 rounded-full mb-4 mx-auto flex items-center justify-center">
                  <ChevronRight className="h-6 w-6 text-yellow-400 rotate-90" />
                </div>
                <h2 className="text-xl font-medium text-gray-500 mb-2">배너 이미지가 없습니다</h2>
                <p className="text-gray-400 mb-4">관리자가 배너 이미지를 추가할 수 있습니다</p>
                <button className="bg-yellow-400 text-white px-4 py-2 rounded-md hover:bg-yellow-500 transition-colors" disabled>
                  관리자 전용
                </button>
              </div>
            </div>
          </div>
        </section>
        
        {/* 카테고리 바로가기 아이콘 */}
        <section className="py-8 bg-yellow-50">
          <div className="container mx-auto px-4">
            <div className="border-l-4 border-yellow-400 pl-3 mb-6">
              <h2 className="text-2xl font-bold">카테고리</h2>
            </div>
            <div className="grid grid-cols-3 md:grid-cols-9 gap-4">
              {categories.map(category => (
                <button 
                  key={category.id}
                  className="flex flex-col items-center p-3 hover:bg-yellow-100 rounded-lg transition"
                >
                  <div className="w-12 h-12 bg-white border-2 border-yellow-200 rounded-full mb-2 flex items-center justify-center">
                    {/* 아이콘 자리 - 나중에 추가 예정 */}
                  </div>
                  <span className="text-sm text-gray-700">{category.name}</span>
                </button>
              ))}
            </div>
          </div>
        </section>
        
        {/* 인기 강의 영역 */}
        <section className="py-8 bg-white">
          <div className="container mx-auto px-4">
            <div className="flex justify-between items-center mb-6">
              <div className="border-l-4 border-yellow-400 pl-3">
                <h2 className="text-2xl font-bold">인기 강의</h2>
              </div>
              <div className="flex space-x-2">
                <button 
                  className={`px-3 py-1 rounded-full text-sm font-medium ${popularTab === 'realtime' ? 'bg-yellow-400 text-white' : 'bg-gray-200 text-gray-700'}`}
                  onClick={() => setPopularTab('realtime')}
                >
                  실시간 인기
                </button>
                <button 
                  className={`px-3 py-1 rounded-full text-sm font-medium ${popularTab === 'weekly' ? 'bg-yellow-400 text-white' : 'bg-gray-200 text-gray-700'}`}
                  onClick={() => setPopularTab('weekly')}
                >
                  주간 인기
                </button>
                <button 
                  className={`px-3 py-1 rounded-full text-sm font-medium ${popularTab === 'monthly' ? 'bg-yellow-400 text-white' : 'bg-gray-200 text-gray-700'}`}
                  onClick={() => setPopularTab('monthly')}
                >
                  월간 인기
                </button>
              </div>
            </div>
            
            <div className="relative">
              <button className="absolute left-0 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full p-2 shadow-md z-10">
                <ChevronLeft className="h-6 w-6 text-gray-700" />
              </button>
              
              <div className="flex space-x-4 overflow-x-auto pb-4 scrollbar-hide">
                <div className="flex-none w-full md:w-auto flex flex-col items-center justify-center bg-white p-12 rounded-lg shadow-sm min-h-64 min-w-96">
                  <div className="w-16 h-16 bg-yellow-100 rounded-full mb-4 flex items-center justify-center">
                    <Book className="h-6 w-6 text-yellow-400" />
                  </div>
                  <p className="text-gray-500 text-center mb-2">아직 등록된 강의가 없습니다</p>
                  <p className="text-gray-400 text-sm text-center mb-4">첫 번째 강의를 업로드해보세요!</p>
                  <button className="bg-yellow-400 text-white px-4 py-2 rounded-md hover:bg-yellow-500 transition-colors">
                    강의 업로드 하기
                  </button>
                </div>
              </div>
              
              <button className="absolute right-0 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full p-2 shadow-md z-10">
                <ChevronRight className="h-6 w-6 text-gray-700" />
              </button>
            </div>
          </div>
        </section>
        
        {/* 숏폼 & 홍보 영상 영역 */}
        <section className="py-8 bg-yellow-50">
          <div className="container mx-auto px-4">
            <div className="flex justify-between items-center mb-6">
              <div className="border-l-4 border-yellow-400 pl-3">
                <h2 className="text-2xl font-bold">숏폼 & 홍보 영상</h2>
              </div>
              <div className="flex space-x-2">
                <button 
                  className={`px-3 py-1 rounded-full text-sm font-medium ${shortVideoTab === 'popular' ? 'bg-yellow-400 text-white' : 'bg-gray-200 text-gray-700'}`}
                  onClick={() => setShortVideoTab('popular')}
                >
                  인기순
                </button>
                <button 
                  className={`px-3 py-1 rounded-full text-sm font-medium ${shortVideoTab === 'latest' ? 'bg-yellow-400 text-white' : 'bg-gray-200 text-gray-700'}`}
                  onClick={() => setShortVideoTab('latest')}
                >
                  최신순
                </button>
                <button 
                  className={`px-3 py-1 rounded-full text-sm font-medium ${shortVideoTab === 'comments' ? 'bg-yellow-400 text-white' : 'bg-gray-200 text-gray-700'}`}
                  onClick={() => setShortVideoTab('comments')}
                >
                  댓글순
                </button>
              </div>
            </div>
            
            <div className="relative">
              <button className="absolute left-0 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full p-2 shadow-md z-10">
                <ChevronLeft className="h-6 w-6 text-gray-700" />
              </button>
              
              <div className="flex space-x-4 overflow-x-auto pb-4 scrollbar-hide">
                <div className="flex-none w-full md:w-auto flex flex-col items-center justify-center bg-white p-12 rounded-lg shadow-sm min-h-64 min-w-96">
                  <div className="w-16 h-16 bg-yellow-100 rounded-full mb-4 flex items-center justify-center">
                    <Video className="h-6 w-6 text-yellow-400" />
                  </div>
                  <p className="text-gray-500 text-center mb-2">아직 등록된 영상이 없습니다</p>
                  <p className="text-gray-400 text-sm text-center mb-4">첫 번째 숏폼 영상을 업로드해보세요!</p>
                  <button className="bg-yellow-400 text-white px-4 py-2 rounded-md hover:bg-yellow-500 transition-colors">
                    숏폼 업로드 하기
                  </button>
                </div>
              </div>
              
              <button className="absolute right-0 top-1/2 transform -translate-y-1/2 bg-white/80 rounded-full p-2 shadow-md z-10">
                <ChevronRight className="h-6 w-6 text-gray-700" />
              </button>
            </div>
          </div>
        </section>
        
        {/* 리뷰 & 후기 섹션 */}
        <section className="py-8 bg-white">
          <div className="container mx-auto px-4">
            <div className="border-l-4 border-yellow-400 pl-3 mb-6">
              <h2 className="text-2xl font-bold">실제 수강생 후기</h2>
            </div>
            
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
              <div className="col-span-full flex flex-col items-center justify-center bg-white p-12 rounded-lg shadow-sm">
                <div className="w-16 h-16 bg-yellow-100 rounded-full mb-4 flex items-center justify-center">
                  <Star className="h-6 w-6 text-yellow-400" />
                </div>
                <p className="text-gray-500 text-center mb-2">아직 작성된 수강생 후기가 없습니다</p>
                <p className="text-gray-400 text-sm text-center">첫 번째 후기의 주인공이 되어보세요!</p>
              </div>
            </div>
          </div>
        </section>
        
        {/* 공지사항 & 이벤트 영역 */}
        <section className="py-8 bg-yellow-50">
          <div className="container mx-auto px-4">
            <div className="flex justify-between items-center mb-6">
              <div className="border-l-4 border-yellow-400 pl-3">
                <h2 className="text-2xl font-bold">공지사항 & 이벤트</h2>
              </div>
              <button className="text-yellow-400 text-sm font-medium">더보기</button>
            </div>
            
            <div className="bg-gray-50 rounded-lg p-12 flex flex-col items-center justify-center">
              <p className="text-gray-500 text-center mb-2">아직 등록된 공지사항이 없습니다</p>
              <p className="text-gray-400 text-sm text-center">새로운 공지사항과 이벤트가 곧 업데이트될 예정입니다</p>
            </div>
          </div>
        </section>
      </main>
      
      {/* 푸터 */}
      <footer className="bg-gray-800 text-white py-8">
        <div className="container mx-auto px-4">
          <div className="flex flex-col md:flex-row justify-between">
            <div className="mb-6 md:mb-0">
              <h2 className="text-xl font-bold mb-4 text-yellow-300">티칭룸 H</h2>
              <p className="text-gray-400 text-sm mb-3">한줄 설명: 관리자가 작성할 예정</p>
              <div className="space-y-2 text-gray-400 text-sm">
                <p className="flex items-center">
                  <span className="w-20">이메일:</span>
                  <span className="text-gray-500">관리자 입력 예정</span>
                </p>
                <p className="flex items-center">
                  <span className="w-20">전화번호:</span>
                  <span className="text-gray-500">관리자 입력 예정</span>
                </p>
                <p className="flex items-center">
                  <span className="w-20">주소:</span>
                  <span className="text-gray-500">관리자 입력 예정</span>
                </p>
              </div>
            </div>
            
            <div className="grid grid-cols-2 md:grid-cols-3 gap-8">
              <div>
                <h3 className="text-lg font-medium mb-3 text-yellow-300">서비스 안내</h3>
                <ul className="space-y-2 text-gray-400 text-sm">
                  <li>이용 가이드</li>
                  <li>정산 가이드</li>
                </ul>
              </div>
              
              <div>
                <h3 className="text-lg font-medium mb-3 text-yellow-300">고객 지원</h3>
                <ul className="space-y-2 text-gray-400 text-sm">
                  <li>자주 묻는 질문</li>
                  <li>1:1 문의</li>
                  <li>공지사항</li>
                </ul>
              </div>
              
              <div>
                <h3 className="text-lg font-medium mb-3 text-yellow-300">회사 정보</h3>
                <ul className="space-y-2 text-gray-400 text-sm">
                  <li>회사 소개</li>
                  <li>이용약관</li>
                  <li>개인정보처리방침</li>
                </ul>
              </div>
            </div>
          </div>
          
          <div className="border-t border-gray-700 mt-8 pt-8 text-center text-gray-400 text-sm">
            <p>© 2025 티칭룸 H. All rights reserved.</p>
          </div>
        </div>
      </footer>
    </div>
  );
}

export default TeachingRoomApp;
